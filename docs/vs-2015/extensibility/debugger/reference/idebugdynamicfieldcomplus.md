---
title: Идебугдинамикфиелдкомплус | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 71756b4c4df0768520f72219cf50e5407604635d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198501"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Представляет динамическое поле для объекта [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## <a name="methods"></a>Методы  
 В дополнение к методам в интерфейсе [идебугдинамикфиелд](../../../extensibility/debugger/reference/idebugdynamicfield.md) этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Извлекает тип по заданному типу-примитиву.|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Извлекает тип с учетом его токена.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
