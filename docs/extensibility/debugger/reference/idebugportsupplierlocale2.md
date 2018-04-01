---
title: IDebugPortSupplierLocale2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
caps.latest.revision: 4
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c39ec782ddfdb8eedfa54c0a274ce92b25c9e1df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Предоставляет поддержку языка для поставщика порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик пользовательский порт реализует этот интерфейс для задания языкового стандарта.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы **IDebugPortSupplierLocale2**.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Задает языковой стандарт для поставщика порта.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)