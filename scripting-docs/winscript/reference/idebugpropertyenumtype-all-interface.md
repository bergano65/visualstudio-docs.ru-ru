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
ms.openlocfilehash: 737d1c5d4279a0a727f79326749dbf14a2fcd4c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574315"
---
# <a name="idebugpropertyenumtype_all-interface"></a>Интерфейс IDebugPropertyEnumType_All
Интерфейсы `IDebugPropertyEnumType` определяются таким образом, чтобы каждый из их идентификаторов IID можно было передавать в качестве фильтра для `IDebugProperty::EnumMembers` при запросе соответствующего перечислителя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Возвращает текстовую строку с описанием имени|  
  
 Следующие интерфейсы наследуют от `IDebugPropertyEnumType_All` и не имеют дополнительных методов.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)