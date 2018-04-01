---
title: IDebugCustomAttributeQuery2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 31df907fe13cd171da8e443d3b8af876adaf3c3f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Определяет существование настраиваемого атрибута для этого поля и, если он существует, возвращает сведения об атрибутах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) для поддержки настраиваемых атрибутов.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Используйте [QueryInterface](/cpp/atl/queryinterface) получить этот интерфейс из [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы **IDebugCustomAttributeQuery** интерфейса.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Определяет, существует ли пользовательский атрибут по имени.|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Возвращает сведения об атрибуте для заданного настраиваемого атрибута.|  
  
 В дополнение к **IDebugCustomAttributeQuery** методы, `IDebugCustomAttributeQuery2` реализует следующий метод:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Возвращает перечислитель для всех настраиваемых атрибутов, вложенные в это поле.|  
  
## <a name="remarks"></a>Примечания  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) метод может возвращать перечислитель для всех настраиваемых атрибутов, определенные для данного поля.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)