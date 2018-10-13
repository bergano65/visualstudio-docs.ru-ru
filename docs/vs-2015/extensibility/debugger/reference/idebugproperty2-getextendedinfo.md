---
title: IDebugProperty2::GetExtendedInfo | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15c9a245c74a32b9ac8e35d774e71f6efc763b7d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197487"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает расширенные сведения для свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] Идентификатор GUID, который определяет тип расширенные сведения, которые требуется извлечь. Дополнительные сведения см. примечания.  
  
 `pExtendedInfo`  
 [out] Возвращает `VARIANT` (C++) или объект (C#), который может использоваться для извлечения сведений о расширенных свойствах. Например, этот параметр может возвращать `IUnknown` интерфейс, который можно запросить для [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) интерфейс. Дополнительные сведения см. примечания.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` Если нет для получения расширенной информации.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется для получения данных, которые не совместима получить, вызвав [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод.  
  
 Следующие идентификаторы GUID обычно распознаются этим методом, (значения GUID задаются для C#, так как имя недоступно в любой сборке). Можно создать дополнительные идентификаторы GUID для внутреннего использования.  
  
|name|Идентификатор GUID|Описание|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Возвращает `IUnknown` интерфейс к документу. Как правило [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) интерфейс может быть получен из этого `IUnknown` интерфейс.|  
|guidCodeContext|{e2fc65e-56ce - 11d 1-b528-00aax004a8797}|Возвращает `IUnknown` интерфейс к контексту документа. Как правило [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейс может быть получен из этого `IUnknown` интерфейс.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Возвращает строку, содержащую идентификатор CLSID пользовательское средство просмотра, обычно реализуют вычислитель выражений.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Возвращает 32-разрядное число, представляющее номер нужного слота, если это свойство представляет локальный адрес управляемого кода.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Возвращает строку, содержащую сигнатуру переменная, связанная с объект свойства.|  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)

