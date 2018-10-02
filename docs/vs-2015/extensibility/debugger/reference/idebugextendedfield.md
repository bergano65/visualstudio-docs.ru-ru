---
title: IDebugExtendedField | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ace5f36ccebc5861c7fe31bba9be41b35a8fdcf5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559456"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugExtendedField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugextendedfield).  
  
Расширяет типы полей, которые доступны для поддержки универсальных типов в управляемом коде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## <a name="methods"></a>Методы  
 В дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Возвращает значение указанного поля расширенного типа.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Определяет, представляет ли поле закрытым типом.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

