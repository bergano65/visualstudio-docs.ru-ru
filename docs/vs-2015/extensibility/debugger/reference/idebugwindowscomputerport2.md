---
title: IDebugWindowsComputerPort2 | Документация Майкрософт
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
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b7788b25b17aa134a3ab9e11b9fcdb66e063f228
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568813"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugWindowsComputerPort2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugwindowscomputerport2).  
  
Позволяет запрашивать сведения о конечном компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется объектами порта диспетчера сеанса отладки.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugWindowsComputerPort2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Извлекает сведения о компьютере, на котором выполняется отладчик.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

