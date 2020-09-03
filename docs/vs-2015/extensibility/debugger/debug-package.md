---
title: Пакет отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dda8b1ac6eaa2cd5352d441600ae720c3aac321c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181290"
---
# <a name="debug-package"></a>Пакет отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакет отладки выполняется в оболочке Visual Studio и обрабатывает весь пользовательский интерфейс. Он использует интерфейсы отладки Visual Studio и взаимодействует с диспетчером отладки сеансов (SDM).  
  
 Прервать события, отправленные через модель SDM, переключит отладчик из режима выполнения в режим прерывания и измените фокус на программу, в которой произошло прерывание. Пакет отладки отслеживает кадр стека и поток из информации, переданной в нее событиями.  
  
 Пакет отладки не имеет зависимостей среды языка или времени выполнения. Нет необходимости реализовывать или изменять пакет отладки.  
  
 Пакет отладки реализуется vsdebug.dll.  
  
## <a name="see-also"></a>См. также:  
 [Диспетчер отладки сеансов](../../extensibility/debugger/session-debug-manager.md)   
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Многопоточно](../../extensibility/debugger/threads.md)   
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)
