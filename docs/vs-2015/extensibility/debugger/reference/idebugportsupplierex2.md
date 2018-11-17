---
title: IDebugPortSupplierEx2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8deeb9ea6e3f1167a55c77ca8af32e2632d5cbe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742610"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Предоставляет поддержку для поставщика порта для выбора и взаимодействовать с core server.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский порт поставщик реализует этот интерфейс, его можно выделить server core для использования.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы **IDebugPortSupplierEx2**.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Задает основной сервер для поставщика порта.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

