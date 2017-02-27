---
title: "IDebugErrorEvent2::GetErrorMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
helpviewer_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает сведения, позволяющий конструкция людск\-четкого сообщения об ошибке.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```c#  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### Параметры  
 `pMessageType`  
 \[out\] возвращает значение [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) перечисление, описывающее тип сообщения.  
  
 `pbstrErrorFormat`  
 \[out\] формат конечного сообщения пользователю \(см. "примечания" подробности\).  
  
 `hrErrorReason`  
 \[out\] код ошибки, сообщение о программе.  
  
 `pdwType`  
 \[out\] серьезность ошибки \(используйте константы для MB\_XXX `MessageBox`; например,  `MB_EXCLAMATION` OR  `MB_WARNING`\).  
  
 `pbstrHelpFileName`  
 \[out\] путь к файлу справки \(набору значение NULL, если файл справки\).  
  
 `pdwHelpId`  
 \[out\] идентификатор раздела справки, который необходимо отобразить \(имеет значение 0, если раздел справки\).  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Сообщение об ошибке должно быть отформатирован вдоль линий `"What I was doing.  %1"`.  `"%1"` затем заменить вызывающим объектом с сообщением об ошибке, полученное из кода ошибки \(который возвращается in  `hrErrorReason`\).  `pMessageType` параметр сообщает вызывающему объекту, как конечное сообщение об ошибке должно быть отображено.  
  
## См. также  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)