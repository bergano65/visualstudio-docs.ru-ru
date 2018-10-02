---
title: IDebugNoSymbolsEvent2 | Документация Майкрософт
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
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1dec7ef8a17a078bc94f41e3270f17ae2cb438a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572788"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugNoSymbolsEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugnosymbolsevent2).  
  
Сигналы [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] отладчика пользовательского интерфейса, чтобы предупредить пользователя, что символы не удалось найти для запущенный исполняемый файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализуется отладчиков и потребляемых [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] отладчика пользовательского интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

