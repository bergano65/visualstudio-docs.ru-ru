---
title: IDebugCustomAttribute | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5db7f060e630c0b4175ecf4708f14fc03869e431
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568942"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет настраиваемый атрибут, и это может дать имя, родительский и тип класса атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс для поддержки настраиваемые атрибуты, связанные с символом. Как правило, он реализован в свой собственный объект.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов [Далее](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) возвращает этот интерфейс. Вызов [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) возвращает [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugCustomAttribute`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Получает поле, к которой подключен текущий атрибут.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Возвращает тип класса настраиваемого атрибута.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Получает имя настраиваемого атрибута.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Возвращает сведения об атрибутах как большой двоичный объект байтов.|  
  
## <a name="remarks"></a>Примечания  
 Настраиваемый атрибут представляет собой структуру для C#, который предоставляет пользовательские метаданные, связанные с определенным классом или методом.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
