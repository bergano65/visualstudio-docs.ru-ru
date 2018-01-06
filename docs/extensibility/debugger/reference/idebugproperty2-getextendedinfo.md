---
title: "IDebugProperty2::GetExtendedInfo | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetExtendedInfo
helpviewer_keywords: IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2d3dfd2111533896db2a3b298ff294ff180d4a70
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Возвращает расширенные сведения для свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidExtendedInfo`  
 [in] Идентификатор GUID, который определяет тип получаемых расширенных сведений. Дополнительные сведения см. заметки.  
  
 `pExtendedInfo`  
 [out] Возвращает `VARIANT` (C++) или объекта (C#), который может использоваться для извлечения сведений о расширенных свойствах. Например, этот параметр может возвращать `IUnknown` интерфейс, который может запрашиваться для [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) интерфейса. Дополнительные сведения см. заметки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` , если нет для получения расширенных сведений.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется с целью получения сведений, непригодны для извлекаемых путем вызова [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод.  
  
 Этот метод (значения GUID задаются для C#, так как имя недоступно в любой сборке) обычно распознает следующие идентификаторы GUID. Дополнительные GUID могут создаваться для внутреннего использования.  
  
|name|Идентификатор GUID|Описание:|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Возвращает `IUnknown` интерфейса в документ. Как правило [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) можно получить из этого интерфейса `IUnknown` интерфейса.|  
|guidCodeContext|{e2fc65e-56ce - 11d 1-b528-00aax004a8797}|Возвращает `IUnknown` интерфейс к контексту документа. Как правило [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) можно получить из этого интерфейса `IUnknown` интерфейса.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Возвращает строку, содержащую CLSID пользовательское средство просмотра, обычно реализуется в средстве оценки выражений.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Возвращает 32-разрядное число, представляющее номер требуемой ячейки, если это свойство представляет локальный адрес управляемого кода.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Возвращает строку, содержащую подпись переменную, связанную с объектом свойства.|  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)