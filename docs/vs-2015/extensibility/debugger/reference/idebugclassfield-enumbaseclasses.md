---
title: 'Идебугклассфиелд:: Енумбасеклассес | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acfdc872ba5f7cf1989ea1d9ec67f82f1c0419b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191044"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает перечислитель для базовых классов этого класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список базовых классов. Возвращает значение null, если базовые классы отсутствуют.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK, возвращает S_SH_NO_BASE_CLASSES, если отсутствуют базовые классы (и `ppEnum` для параметра задано значение null); в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Базовые классы в объекте перечислителя указываются в порядке наиболее быстрого (или самого производного) базового класса до самого удаленного базового класса. Например, при наличии классов C++:  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 Перечисление вернет базовые классы в порядке `Level2` , `Level1` , `Root` .  
  
## <a name="see-also"></a>См. также:  
 [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
