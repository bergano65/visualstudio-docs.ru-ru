---
title: "DisassemblyData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DisassemblyData"
helpviewer_keywords: 
  - "Структура DisassemblyData"
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# DisassemblyData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает одну инструкцию дизассемблированный код для интегрированной среды разработки \(ide\) для отображения.  
  
## Синтаксис  
  
```cpp#  
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
  
```c#  
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
  
## Члены  
 `dwFields`  
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) константа, указывающая, какие поля заполнянны.  
  
 `bstrAddress`  
 Адрес в качестве смещения относительно определенной начальной точки \(обычно начала присоединенной функции\).  
  
 `bstrCodeBytes`  
 Байты кода для этой инструкции.  
  
 `bstrOpcode`  
 Код операции для инструкции.  
  
 `bstrOperands`  
 Операнды для этой инструкции.  
  
 `bstrSymbol`  
 Имя символа, при наличии таковой, связанное с адресом \(открытыми символом, метки и т д\).  
  
 `uCodeLocationId`  
 Идентификатор расположение кода для этой демонтированной линии.  Если адрес контекста кода одной линии больше адрес контекста кода других, демонтированный идентификатор расположение кода первого также будет больше, чем идентификатор расположение кода второго.  
  
 `posBeg`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) это соответствует позиции в документе, в котором начинаются данные дизассемблированный код.  
  
 `posEnd`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) это соответствует позиции в документе, в котором данные дизассемблированный код завершения.  
  
 `bstrDocumentUrl`  
 Для текстовых документов, которые можно представить как имена файлов `bstrDocumentUrl` поле заполнено именем файла, где источник можно найти, используя формат  `имя file://file`.  
  
 Для текстовых документов, которые не могут быть представлены как имена файлов `bstrDocumentUrl` уникальный идентификатор документа и отладчик должен реализовать  [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) метод.  
  
 Это поле также может содержать дополнительную информацию о контрольных суммах.  Дополнительные сведения см. в разделе " примечания ".  
  
 `dwByteOffset`  
 Число байт, инструкция с начала линии кода.  
  
 `dwFlags`  
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) константа, которая определяет, какие флаги активным.  
  
## Заметки  
 Каждое `DisassemblyData` структура описывает одну инструкцию дизассемблированный код.  Массив возвращается из этих структур [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) метод.  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) структура используется для документов, основываясь только текст.  Диапазон исходного кода для этой инструкции заполнянно только для первой инструкции, созданную из выписки или линий, например, когда `dwByteOffset == 0`.  
  
 Для документов, non\-текстуальны, контекст рисования можно получить из кода. `bstrDocumentUrl` поле должно быть значение NULL.  Если `bstrDocumentUrl` поле аналогичен  `bstrDocumentUrl` поле в предыдущей  `DisassemblyData` элемент массива, затем присвойте  `bstrDocumentUrl` в значение NULL.  
  
 Если `dwFlags` поле обладает  `DF_DOCUMENT_CHECKSUM` набор, затем пометить дополнительные сведения о контрольной сумме за строкой, указанной в  `bstrDocumentUrl` поле.  В частности, признака конца строки со значением NULL, то следуйте GUID, задающее алгоритм контрольной суммы, который, в свою очередь, указывающими за 4 байта число байтов в контрольной суммы, и, в свою очередь, соответствует байт контрольной суммы.  См. пример в этом разделе для кодирования и декодирования это поле [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
## Пример  
 `bstrDocumentUrl` это поле может содержать дополнительную информацию, за исключением строки, если  `DF_DOCUMENT_CHECKSUM` пометить задан.  Процесс создания и чтение эта кодируемая строка является прямолинейным in [!INCLUDE[vcprvc](../../../debugger/includes/vcprvc_md.md)].  Однако в пределах [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]дело в другое.  Для тех, любознательни следующем примере показан один из способов создания кодируемая строка из [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] одним способом расшифровки и закодированную строку внутри  [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].  
  
```c#  
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
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)