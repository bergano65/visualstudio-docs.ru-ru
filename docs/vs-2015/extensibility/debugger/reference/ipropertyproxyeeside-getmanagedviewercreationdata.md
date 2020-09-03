---
title: 'Ипропертипроксеесиде:: Жетманажедвиеверкреатиондата | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5161894875ac683e5a6e49ae623bd6025531006
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199530"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает сведения о средстве просмотра для этого типа свойства, чтобы создать экземпляр этого средства просмотра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
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
 заполняет Возвращает имя сборки, содержащей этот объект.  
  
 `assemBytes`  
 заполняет Возвращает объект [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) , содержащий байты сборки данного объекта (это значение null, если нет доступных байтов).  
  
 `assemPdb`  
 заполняет Возвращает `IEEDataStorage` объект, содержащий сведения о хранилище символов для этого объекта (значение null, если хранилище символов недоступно).  
  
 `className`  
 заполняет Возвращает имя класса, содержащего этот объект.  
  
 `alr`  
 заполняет Возвращает значение из перечисления [ассемблилокресолутион](../../../extensibility/debugger/reference/assemblylocresolution.md) , указывающее расположение сборки.  
  
 `replacementOk`  
 заполняет Возвращает ненулевой ( `TRUE` ), если значение этого объекта может быть изменено; ноль ( `FALSE` ), если объект доступен только для чтения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод используется визуализаторами типов для создания экземпляра управляемого средства просмотра.  
  
## <a name="see-also"></a>См. также:  
 [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ассемблилокресолутион](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
