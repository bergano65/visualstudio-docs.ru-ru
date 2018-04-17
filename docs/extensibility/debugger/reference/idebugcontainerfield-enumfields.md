---
title: IDebugContainerField::EnumFields | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0af939253de7b592e7c0ec35be9ea2b9bbff2b0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Создает перечислитель для полей контейнера.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwKindFilter`  
 [in] Сочетание [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) константы, выберите поля, которые необходимо перечислить. Типы полей можно описать типы хранилищ, например класса или типом-примитивом или определенные сведения, такие как local, параметр или указатель «this».  
  
 `dwModifiersFilter`  
 [in] Сочетание [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) константы, выберите поля, которые необходимо перечислить. Модификаторы поля может быть разрешений на доступ, например, public или private или хранилища сведения, такие как виртуальные, static или final.  
  
 `pszNameFilter`  
 [in] Имя поля для перечисления. Это может быть значение null, если все поля должны быть возвращены.  
  
 `nameMatch`  
 [in] Значение из [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) перечисления, которое определяет, является ли поиск с учетом регистра или нет.  
  
 `ppEnum`  
 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий собой список полей. Возвращает значение null, если нет ни одного поля.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает S_OK или S_FALSE, если нет ни одного поля. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 `dwKindFilter`, `dwModifiersFilter`, И `pszNameFilter` параметры можно объединить, например, чтобы выбрать все открытые виртуальные методы, с именем «MyMethod».  
  
## <a name="see-also"></a>См. также  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)