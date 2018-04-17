---
title: IDebugCustomAttribute | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0d7497f5fcda3b871c5a1ad57cf04767617bdab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Этот интерфейс представляет настраиваемый атрибут, и он может предоставить имя, родительский и тип класса атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс для поддержки настраиваемые атрибуты, связанные с символом. Обычно реализуется в своем объекте.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [Далее](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) возвращает этот интерфейс. Вызов [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) возвращает [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugCustomAttribute`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Возвращает поле, к которой подключен текущий атрибут.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Возвращает тип класса настраиваемого атрибута.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Возвращает имя настраиваемого атрибута.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Возвращает сведения об атрибутах, как большой двоичный объект байтов.|  
  
## <a name="remarks"></a>Примечания  
 Настраиваемый атрибут — это структура, для C#, предоставляющий пользовательские метаданные, связанные с определенным классом или метода.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)