---
title: Отладка пакета | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ca438b7ed8c9b6a4b84693f975144040f998f01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110033"
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