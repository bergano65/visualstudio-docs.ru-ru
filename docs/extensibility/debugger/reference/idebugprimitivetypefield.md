---
title: IDebugPrimitiveTypeField | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6bad8b67d766b18a217fbdccd5ae3fdd5f7ec19
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934048"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Представляет значение примитивного типа перечисления из [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPrimitiveTypeField : IDebugField  
```  
  
## <a name="methods"></a>Методы  
 В дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, этот интерфейс реализует следующий метод:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Извлекает тип-примитив, связанные с этим полем.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll