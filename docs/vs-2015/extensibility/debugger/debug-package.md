---
title: Отладка пакета | Документация Майкрософт
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
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cae13349dd234f46e1d9de1589fcb50f1e5b0aef
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793455"
---
# <a name="debug-package"></a>Пакет отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отладочный пакет выполняется в оболочке Visual Studio и отвечает за выполнение всех пользовательского интерфейса. Он использует интерфейсы отладки Visual Studio и взаимодействует с диспетчер отладки сеансов (SDM).  
  
 События прерывания, проходящие через SDM переключиться отладчик из режима выполнения в режим приостановки выполнения и изменения фокуса в программу разрыва. Размер пакета отладки отслеживает кадр стека и поток из сведения, отправляемые на него с помощью событий.  
  
 Размер пакета отладки не имеет языка и зависимостей среды выполнения. Необязательно для реализации или изменить размер пакета отладки.  
  
 Размер пакета отладки реализуется vsdebug.dll.  
  
## <a name="see-also"></a>См. также  
 [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)   
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Потоки](../../extensibility/debugger/threads.md)   
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)

