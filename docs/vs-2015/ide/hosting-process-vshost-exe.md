---
title: Ведущий процесс (vshost.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a998246f514f13a575f6a7fef850f9f705f92553
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645531"
---
# <a name="hosting-process-vshostexe"></a>Главный процесс (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ведущий процесс — это возможность Visual Studio, которая улучшает эффективность отладки, позволяя отладку с частичным доверием и вычисление выражений времени разработки. Файлы ведущего процесса содержат "vshost" в своем имени и помещаются в выходную папку проекта. Дополнительные сведения см. [в разделе Отладка и ведущий процесс](../debugger/debugging-and-the-hosting-process.md).

> [!NOTE]
> Файлы ведущего процесса (.vshost.exe) предназначены для использования в Visual Studio и не должны напрямую запускаться и развертываться вместе с вашим приложением.

## <a name="improved-debugging-performance"></a>Улучшенная производительность отладки
 Ведущий процесс создает домен приложения и связывает отладчик с приложением. Выполнение этих задач может привести к значительной задержке между запуском отладки и началом выполнения приложения. Ведущий процесс позволяет повысить производительность, создав домен приложения, сопоставив отладчик в фоновом режиме, а также сохраняя состояние домена приложения и отладчика между запусками приложения. Дополнительные сведения о доменах приложений см. в разделе [домены приложений](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).

## <a name="partial-trust-debugging"></a>Отладка с частичным доверием
 На странице [Безопасность](../ide/reference/security-page-project-designer.md) в **конструкторе проектов** приложение может быть указано как имеющее частичное доверие. Для отладки такого приложения требуется отдельная инициализация домена приложения. Эта инициализация обрабатывается ведущим процессом.

## <a name="design-time-expression-evaluation"></a>Вычисление выражений в процессе разработки
 Вычисление выражений во время разработки позволяет тестировать код в окне **интерпретации** без запуска приложения. Ведущий процесс выполняет этот код при вычислении выражений во время разработки. Дополнительные сведения см. в разделе [Immediate Window](../ide/reference/immediate-window.md).

## <a name="see-also"></a>См. также:
 [Отладка и процесс размещения](../debugger/debugging-and-the-hosting-process.md) [. как отключить](../ide/how-to-disable-the-hosting-process.md) [домены приложения](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8) [интерпретации](../ide/reference/immediate-window.md) ведущего процесса
