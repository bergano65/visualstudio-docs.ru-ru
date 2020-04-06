---
title: РазборкаДанные (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737282"
---
# <a name="disassemblydata"></a>DisassemblyData
Описывает одну инструкцию по разборке для отображения интегрированной среды разработки (IDE).

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Участники
`dwFields`\
Константа [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) определяет, какие поля заполнены.

`bstrAddress`\
Адрес как смещение от какой-то отправной точки (обычно начало связанной функции).

`bstrCodeBytes`\
Код байт для этой инструкции.

`bstrOpcode`\
Opcode для этой инструкции.

`bstrOperands`\
Операнды для этой инструкции.

`bstrSymbol`\
Имя символа, если таковое имеется, связано с адресом (общественный символ, этикетка и так далее).

`uCodeLocationId`\
Идентификатор местоположения кода для этой разобранной строки. Если адрес контекста кода одной строки больше, чем код-контекстный адрес другой, то разобранный идентификатор местоположения кода первой также будет больше, чем идентификатор местоположения кода второй.

`posBeg`\
[TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) которая соответствует позиции в документе, где начинается разборка данных.

`posEnd`\
[TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) которая соответствует позиции в документе, где заканчивается разборка данных.

`bstrDocumentUrl`\
Для текстовых документов, которые могут `bstrDocumentUrl` быть представлены как имена файлов, поле заполняется именем файла, где можно найти источник, используя формат. `file://file name`

Для текстовых документов, которые не `bstrDocumentUrl` могут быть представлены в качестве имен файлов, является уникальным идентификатором для документа, и движок отладки должен реализовать метод [GetDocument.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)

Это поле также может содержать дополнительную информацию о чеках. Дополнительные сведения см. в разделе "Примечания".

`dwByteOffset`\
Количество байтов инструкции от начала строки кода.

`dwFlags`\
DISASSEMBLY_FLAGS [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) константа, которая определяет, какие флаги активны.

## <a name="remarks"></a>Примечания
Каждая `DisassemblyData` структура описывает одну инструкцию разборки. Массив этих структур возвращается из метода [чтения.](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)

Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) используется только для текстовых документов. Диапазон исходного кода для этой инструкции заполняется только для первой инструкции, `dwByteOffset == 0`генерируемой из оператора или строки, например, когда .

Для нетекстовых документов из кода может быть получен контекст документа, а `bstrDocumentUrl` поле должно быть нулевым значением. Если `bstrDocumentUrl` поле такое же, как и `bstrDocumentUrl` поле в предыдущем `DisassemblyData` элементе массива, установите `bstrDocumentUrl` значение null.

Если `dwFlags` поле имеет `DF_DOCUMENT_CHECKSUM` набор флага, то дополнительная информация `bstrDocumentUrl` о проверке следует строке, на которую указывает поле. В частности, после терминатора нулевой строки, следует GUID, определяющий алгоритм проверки, за которым, в свою очередь, следует значение 4 байт с указанием количества байтов в чексуме и которое, в свою очередь, сопровождается байтами чекса. Смотрите пример в этой теме о том, как [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]кодировать и расшифровывать это поле в .

## <a name="example"></a>Пример
Поле `bstrDocumentUrl` может содержать дополнительную информацию, `DF_DOCUMENT_CHECKSUM` кроме строки, если флаг установлен. Процесс создания и чтения этой закодированной [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]строки прост в . Однако, [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]в , это другой вопрос. Для тех, кому интересно, следующий пример показывает один способ [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] создания закодированной строки из [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]и один способ расшифровать закодированную строку в .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Прочитать](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
