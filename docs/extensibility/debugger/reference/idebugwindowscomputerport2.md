---
title: IDebugWindowsComputerPort2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e2a037ad0477be258e33879d1dc336fa67cc915
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965292"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Позволяет запрашивать сведения о конечном компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется объектами порта диспетчера сеанса отладки.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugWindowsComputerPort2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Извлекает сведения о компьютере, на котором выполняется отладчик.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll