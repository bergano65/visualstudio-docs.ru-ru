---
title: "IDebugProperty2::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает расширенные сведения для свойства.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```c#  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### Параметры  
 `guidExtendedInfo`  
 \[in\] идентификатор GUID, определяющий тип расширенного сведения, которые необходимо извлечь.  Дополнительные сведения см. в разделе " примечания ".  
  
 `pExtendedInfo`  
 \[out\] возвращает a `VARIANT` \(C\+\+\) или объект \(c\#\), который можно использовать для получения сведений о расширенного свойства.  Например, этот параметр может возвращать `IUnknown` интерфейс, который можно запросить  [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) интерфейс.  Дополнительные сведения см. в разделе " примечания ".  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` если подробные данные, которые необходимо извлечь.  
  
## Заметки  
 Этот метод для получения сведений, не одалживает к требуется извлечь путем вызова [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод.  
  
 Следующие GUID обычно распознаются этим методом, указаны значения GUID \(для c\#, так как имя недоступно в любой сборке\).  Дополнительные GUID может быть создан для внутреннего использования.  
  
|Имя|GUID|Описание|  
|---------|----------|--------------|  
|guidDocument|{3f98de84\-fee9\-11d0\-b47f\-00a0244a1dd2}|Возвращает `IUnknown` интерфейс к документу.  Обычно [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) интерфейс быть получен от данного  `IUnknown` интерфейс.|  
|guidCodeContext|{e2fc65e\-56ce\-11d1\-b528\-00aax004a8797}|Возвращает `IUnknown` интерфейс к контексту документа.  Обычно [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейс быть получен от данного  `IUnknown` интерфейс.|  
|guidCustomViewerSupported|{d9c9da31\-ffbe\-4eeb\-9186\-23121e3c088c}|Возвращает строку, содержащую идентификатор CLSID пользовательского средства просмотра, как правило, предоставляемого средством оценки выражений.|  
|guidExtendedInfoSlot|{6df235ad\-82c6\-4292\-9c97\-7389770bc42f}|Возвращает 32 число, представляющее нужный число слотов если это свойство представляет локальный адрес управляемого кода.|  
|guidExtendedInfoSignature|{b5fb6d46\-f805\-417f\-96a3\-8ba737073ffd}|Возвращает строку, содержащую сигнатуру переменной, связанного с объектом свойства.|  
  
## См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)