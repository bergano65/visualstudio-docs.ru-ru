---
title: IDebugDynamicFieldCOMPlus | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
caps.latest.revision: 6
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3f5f04c65e9e5799c759dd5a77d7158c98b9d46d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
Представляет динамическое поле [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## <a name="methods"></a>Методы  
 В дополнение к методам на [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Возвращает тип, заданный тип-примитив.|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Возвращает тип, указанному токену.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll