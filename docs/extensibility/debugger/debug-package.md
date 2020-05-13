---
title: Пакет отлавы Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739020"
---
# <a name="debug-package"></a>Пакет debug
Пакет отладки работает в оболочке Visual Studio и обрабатывает весь uI. Он потребляет интерфейсы отладки Visual Studio и общается с менеджером отладки сеанса (SDM).

 События разрыва, отправляемые через SDM, переключают отладчик из режима запуска в режим разрыва и меняют фокус на программу, в которой произошел разрыв. Пакет отладки отслеживает кадр стека и поток из информации, отправленной ему событиями.

 Пакет отладки не имеет зависимостей среды языка или времени выполнения. Нет необходимости реализовывать или изменять пакет отладки.

 Пакет отладки реализован *vsdebug.dll.*

## <a name="see-also"></a>См. также
- [Менеджер отладки сеанса](../../extensibility/debugger/session-debug-manager.md)
- [Стек кадры](../../extensibility/debugger/stack-frames.md)
- [Потоков](../../extensibility/debugger/threads.md)
- [Компоненты debugger](../../extensibility/debugger/debugger-components.md)
