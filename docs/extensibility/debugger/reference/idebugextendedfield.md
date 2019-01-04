---
title: IDebugExtendedField | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a503ff99542215ba5922feb860fc04cd047ce287
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869678"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Расширяет типы полей, которые доступны для поддержки универсальных типов в управляемом коде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## <a name="methods"></a>Методы  
 В дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Возвращает значение указанного поля расширенного типа.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Определяет, представляет ли поле закрытым типом.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll