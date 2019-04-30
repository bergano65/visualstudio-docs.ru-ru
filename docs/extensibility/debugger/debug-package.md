---
title: Отладка пакета | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ba784f3a544b2f66f1f2c9c229f85477bf6c782
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890043"
---
# <a name="debug-package"></a>Отладка пакета
Отладочный пакет выполняется в оболочке Visual Studio и отвечает за выполнение всех пользовательского интерфейса. Он использует интерфейсы отладки Visual Studio и взаимодействует с диспетчер отладки сеансов (SDM).

 События прерывания, проходящие через SDM переключиться отладчик из режима выполнения в режим приостановки выполнения и изменения фокуса в программу разрыва. Размер пакета отладки отслеживает кадр стека и поток из сведения, отправляемые на него с помощью событий.

 Размер пакета отладки не имеет языка и зависимостей среды выполнения. Необязательно для реализации или изменить размер пакета отладки.

 Размер пакета отладки реализуется *vsdebug.dll*.

## <a name="see-also"></a>См. также
- [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)
- [Кадры стека](../../extensibility/debugger/stack-frames.md)
- [Потоки](../../extensibility/debugger/threads.md)
- [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)