---
title: IDebugPortSupplierLocale2 | Документация Майкрософт
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
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f1afac07a30b026fda824284f201b86b95709f2b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573211"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugPortSupplierLocale2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplierlocale2).  
  
Предоставляет поддержку языка для поставщика порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский порт поставщик реализует этот интерфейс для задания языкового стандарта.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы **IDebugPortSupplierLocale2**.  
  
|Метод|Описание|  
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

