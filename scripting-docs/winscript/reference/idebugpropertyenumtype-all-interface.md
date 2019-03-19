---
title: Интерфейс IDebugPropertyEnumType_All | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ddd9fb24aa83a6027d6d705de6a748a96b2e28
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149305"
---
# <a name="idebugpropertyenumtypeall-interface"></a>Интерфейс IDebugPropertyEnumType_All
`IDebugPropertyEnumType` Интерфейсы определяются таким образом, каждый из их идентификаторы IID можно передать в качестве фильтра для `IDebugProperty::EnumMembers` при запросе соответствующим перечислителем.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Возвращает текстовую строку, описывающую имя|  
  
 Следующие интерфейсы наследуются из `IDebugPropertyEnumType_All`, и нет дополнительных методов.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)