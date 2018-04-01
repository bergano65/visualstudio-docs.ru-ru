---
title: IDebugGenericFieldInstance | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3d5ee0d66f1248ec3770dd9402baaa1dc8066e96
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
Представляет экземпляр поля для универсального типа управляемого кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugGenericFieldInstance : IUnknown  
```  
  
## <a name="methods"></a>Методы  
 Этот интерфейс реализует следующие методы:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|Получает аргументы параметра типа для этого экземпляра.|  
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|Возвращает число типа параметра аргументы для данного экземпляра.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll