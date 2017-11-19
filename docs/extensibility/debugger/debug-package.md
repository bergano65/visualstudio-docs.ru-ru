---
title: "Отладка пакета | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eccd258476f82871732ef7b16f0282d2f945b9ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="debug-package"></a>Отладка пакета
Отладочный пакет работает в оболочке Visual Studio и обрабатывает все пользовательского интерфейса. Он использует интерфейсы отладки Visual Studio и взаимодействует с диспетчером сеанса отладки (SDM).  
  
 Break события, отправляемые через SDM переключение отладчик из режима выполнения в режим приостановки выполнения и изменения фокуса в программу разрыва. Отладочный пакет отслеживает кадр стека и поток из сведения, передаваемые с помощью событий.  
  
 Отладочный пакет не имеет языка или зависимости среды выполнения. Необязательно для реализации или изменить пакет отладки.  
  
 Отладочный пакет реализуется vsdebug.dll.  
  
## <a name="see-also"></a>См. также  
 [Диспетчер сеансов отладки](../../extensibility/debugger/session-debug-manager.md)   
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Потоки](../../extensibility/debugger/threads.md)   
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)