---
title: "IPropertyProxyEESide::GetManagedViewerCreationData | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords: IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc4d81470a1ea15573171a80034efcd6daf720ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Извлекает сведения о средстве просмотра для этого типа свойства для создания экземпляра этого средства просмотра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `assemName`  
 [out] Возвращает имя сборки, содержащий этот объект.  
  
 `assemBytes`  
 [out] Возвращает [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, содержащий байты сборки этого объекта (это значение null, если байты не доступны).  
  
 `assemPdb`  
 [out] Возвращает `IEEDataStorage` объект, содержащий символ хранить сведения для этого объекта (это значение null при наличии не хранилища символов).  
  
 `className`  
 [out] Возвращает имя класса, содержащий этот объект.  
  
 `alr`  
 [out] Возвращает значение из [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) перечисление, указывающее расположение сборки.  
  
 `replacementOk`  
 [out] Возвращает ненулевое значение (`TRUE`), если значение этого объекта можно изменить; ноль (`FALSE`), если объект доступен только для чтения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется с визуализаторами типов для создания экземпляра управляемого просмотра.  
  
## <a name="see-also"></a>См. также  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)