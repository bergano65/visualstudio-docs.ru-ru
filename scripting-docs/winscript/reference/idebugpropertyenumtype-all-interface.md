---
title: Интерфейс IDebugPropertyEnumType_All | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 75de35bd42ea91e7d27523ba42c392650686041a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726814"
---
# <a name="idebugpropertyenumtypeall-interface"></a>Интерфейс IDebugPropertyEnumType_All
`IDebugPropertyEnumType` Определенные интерфейсы, чтобы каждый их IID можно передавать в качестве фильтра для `IDebugProperty::EnumMembers` при запросе соответствующим перечислителем.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Возвращает текстовую строку, описывающую имя|  
  
 Следующие интерфейсы наследуются от класса `IDebugPropertyEnumType_All`, и дополнительные методы не имеют.  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)