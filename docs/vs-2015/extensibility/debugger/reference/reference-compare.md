---
title: REFERENCE_COMPARE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- REFERENCE_COMPARE
helpviewer_keywords:
- REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d617d428c9551bc821e1c72fa517497769e6f047
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204922"
---
# <a name="reference_compare"></a>REFERENCE_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает тип сравнения для ссылок.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
typedef DWORD REFERENCE_COMPARE;  
```  
  
```csharp  
public enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
```  
  
## <a name="members"></a>Участники  
 REF_COMPARE_EQUAL  
 Задает сравнение равенства.  
  
 REF_COMPARE_LESS_THAN  
 Указывает сравнение "меньше чем".  
  
 REF_COMPARE_GREATER_THAN  
 Задает сравнение "больше чем".  
  
## <a name="remarks"></a>Remarks  
 Передается в качестве аргумента в метод [Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Сравнить](../../../extensibility/debugger/reference/idebugreference2-compare.md)
