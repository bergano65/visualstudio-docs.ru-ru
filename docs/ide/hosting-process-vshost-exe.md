---
title: Ведущий процесс (vshost.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bba0463870f4d615e45d8f2c11071bfd8a1b8009
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="hosting-process-vshostexe"></a>Ведущий процесс (vshost.exe)

Ведущий процесс — это возможность Visual Studio, которая улучшает эффективность отладки, позволяя отладку с частичным доверием и вычисление выражений времени разработки. Файлы ведущего процесса содержат *vshost* в своих именах и помещаются в выходную папку проекта. Дополнительные сведения см. в статье [Отладка и ведущий процесс](../debugger/debugging-and-the-hosting-process.md).

> [!NOTE]
> Файлы ведущего процесса (*.vshost.exe*) предназначены для использования в Visual Studio и не должны напрямую запускаться и развертываться вместе с вашим приложением.

## <a name="improved-debugging-performance"></a>Улучшенная производительность отладки
 Ведущий процесс создает домен приложения и связывает отладчик с приложением. Выполнение этих задач может привести к значительной задержке между запуском отладки и началом выполнения приложения. Ведущий процесс позволяет повысить производительность, создав домен приложения, сопоставив отладчик в фоновом режиме, а также сохраняя состояние домена приложения и отладчика между запусками приложения. Дополнительные сведения о доменах приложений см. в статье [Домены приложений](/dotnet/framework/app-domains/application-domains).

## <a name="partial-trust-debugging"></a>Отладка с частичным доверием
 На странице [Безопасность](../ide/reference/security-page-project-designer.md) в **конструкторе проектов** приложение может быть указано как имеющее частичное доверие. Для отладки такого приложения требуется отдельная инициализация домена приложения. Эта инициализация обрабатывается ведущим процессом.

## <a name="design-time-expression-evaluation"></a>Вычисление выражений в процессе разработки
 Вычисление выражений во время разработки позволяет тестировать код в окне **интерпретации** без запуска приложения. Ведущий процесс выполняет этот код при вычислении выражений во время разработки. Дополнительные сведения см. в статье [Окно интерпретации](../ide/reference/immediate-window.md).

## <a name="see-also"></a>См. также

- [Отладка и процесс размещения](../debugger/debugging-and-the-hosting-process.md)
- [Практическое руководство. Отключение ведущего процесса](../ide/how-to-disable-the-hosting-process.md)
- [Окно интерпретации](../ide/reference/immediate-window.md)
- [Домены приложений](/dotnet/framework/app-domains/application-domains)