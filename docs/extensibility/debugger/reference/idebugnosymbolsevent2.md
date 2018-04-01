---
title: IDebugNoSymbolsEvent2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 6
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4c103cdfec8d93c8b43106d5e2b3757750ffda70
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Сигналы [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладчика пользовательского интерфейса, чтобы предупредить пользователя о том, что символы не удалось найти для запущенный исполняемый файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализуемый отладчики и используемый [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса отладчика.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll