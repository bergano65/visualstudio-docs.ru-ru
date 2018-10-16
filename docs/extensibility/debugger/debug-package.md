---
title: Отладка пакета | Документация Майкрософт
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
ms.openlocfilehash: 04eb6802cabd4ae36151580c573d28b977ca348e
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204048"
---
# <a name="debug-package"></a>Отладка пакета
Отладочный пакет выполняется в оболочке Visual Studio и отвечает за выполнение всех пользовательского интерфейса. Он использует интерфейсы отладки Visual Studio и взаимодействует с диспетчер отладки сеансов (SDM).  
  
 События прерывания, проходящие через SDM переключиться отладчик из режима выполнения в режим приостановки выполнения и изменения фокуса в программу разрыва. Размер пакета отладки отслеживает кадр стека и поток из сведения, отправляемые на него с помощью событий.  
  
 Размер пакета отладки не имеет языка и зависимостей среды выполнения. Необязательно для реализации или изменить размер пакета отладки.  
  
 Размер пакета отладки реализуется *vsdebug.dll*.  
  
## <a name="see-also"></a>См. также  
 [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)   
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Потоки](../../extensibility/debugger/threads.md)   
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)