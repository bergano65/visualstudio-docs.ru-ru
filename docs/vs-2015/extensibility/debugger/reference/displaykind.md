---
title: DisplayKind | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 10bed6b3398b93b0776876491d812ec36c9e9e04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198806"
---
# <a name="displaykind"></a>DisplayKind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Перечисляет допустимые значения, представляющие типы данных с [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта и отображать для пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
typedef DWORD DisplayKind;  
```  
  
```csharp  
public enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 DisplayKind_Value  
 Значение поля.  
  
 DisplayKind_Name  
 Имя поля.  
  
 DisplayKind_Type  
 Тип поля.  
  
## <a name="requirements"></a>Требования  
 Заголовок: EE.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)
