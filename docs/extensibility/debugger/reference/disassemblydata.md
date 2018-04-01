---
title: DisassemblyData | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0e97d2cc15e3b613fa56d2d4df1d5df8c68f9b06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="disassemblydata"></a>DisassemblyData
Описывает одну инструкцию Дизассемблированный код для интегрированной среды разработки (IDE) для отображения.  
  
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
 `dwFields`  
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) константа, указывающая, какие поля заполнены.  
  
 `bstrAddress`  
 Адрес как смещение от некоторых начальной точки (обычно начало соответствующего функции).  
  
 `bstrCodeBytes`  
 Байты кода для данной инструкции.  
  
 `bstrOpcode`  
 Код операции для данной инструкции.  
  
 `bstrOperands`  
 Операнды для данной инструкции.  
  
 `bstrSymbol`  
 Имя символа, если таковые имеются, связанные с адресом (открытых символов, метки и т. д.).  
  
 `uCodeLocationId`  
 Идентификатор кодовой расположение для этой строки дизассемблированные. Если адрес контекст кода одной строки больше, чем адрес контекст кода другого идентификатора расположения дизассемблированного кода первого будет больше, чем второй идентификатор расположение кода.  
  
 `posBeg`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , соответствующий позицию в документе, в котором начинаются данные Дизассемблированный код.  
  
 `posEnd`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , соответствующий позицию в документе, в которой заканчивается данных Дизассемблированный код.  
  
 `bstrDocumentUrl`  
 Для текстовых документов, которые могут быть представлены как имена файлов `bstrDocumentUrl` вводится имя файла, где можно найти источник, используя формат `file://file name`.  
  
 Для текстовых документов, которые не могут быть представлены как имена файлов `bstrDocumentUrl` — это уникальный идентификатор для документа, и отладчик должен реализовывать [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) метод.  
  
 Это поле также может содержать дополнительные сведения о контрольных суммах. Дополнительные сведения см. заметки.  
  
 `dwByteOffset`  
 Число байтов, которые инструкция считается от начала строки кода.  
  
 `dwFlags`  
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) константа, указывающая, какие флаги активны.  
  
## <a name="remarks"></a>Примечания  
 Каждый `DisassemblyData` структура описывает одну инструкцию Дизассемблированный код. Возвращенный массив этих структур [чтения](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) метод.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) использовать структуру текстовых только для документов. Исходный код диапазон для данной инструкции заполняется только для первой инструкции, созданные из оператора или строки, например, если `dwByteOffset == 0`.  
  
 Для документов, которые являются нетекстовые, к контексту документа можно получить из кода и `bstrDocumentUrl` поле должно иметь значение null. Если `bstrDocumentUrl` поля совпадает со значением `bstrDocumentUrl` поля в предыдущем `DisassemblyData` элемента массива, а затем задайте `bstrDocumentUrl` со значением null.  
  
 Если `dwFlags` поле имеет `DF_DOCUMENT_CHECKSUM` набор флагов, а затем сведения о контрольной сумме дополнительных следует строка, на который указывает `bstrDocumentUrl` поля. В частности после конца строки null, следует идентификатор GUID, определяющий алгоритма подсчета контрольной суммы, в свою очередь следуют 4-байтовым значение, указывающее число байтов в контрольной суммы и, в свою очередь следуют байт контрольной суммы. См. пример в этом разделе о том, как для кодирования и декодирования этого поля в [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
## <a name="example"></a>Пример  
 `bstrDocumentUrl` Поле может содержать дополнительную информацию, кроме строки, если `DF_DOCUMENT_CHECKSUM` установлен флаг. Процесс создания и чтения этого закодированную строку достаточно прост в [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]. Однако в [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)], он представляет собой отдельную задачу. Для тех, кто интересует, в примере показан один из способов создания закодированную строку из [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] и один из способов декодировать закодированную строку в [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
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
            for (int i = 0; i < guidDataLength; i++)  
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
  
               // Parse string out.  String is assumed to be Unicode.  
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
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
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
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)