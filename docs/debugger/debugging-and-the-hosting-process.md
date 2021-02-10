---
title: Отладка и ведущий процесс | Документы Майкрософт
description: Для версий Visual Studio, предшествующих 2017, используется процесс размещения, чтобы улучшить рабочие характеристики отладчика и получить доступ к некоторым его возможностям.
ms.custom: SEO-VS-2020
ms.date: 08/01/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 750b210ce04850e0cb6370094cdcc835f577b587
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872876"
---
# <a name="debugging-and-the-hosting-process"></a>Отладка и процесс размещения
В процессе размещения Visual Studio предусмотрены средства улучшения рабочих характеристик отладчика и новые возможности отладки, например, отладка с частичным доверием и вычисление выражения во время разработки. При необходимости процесс размещения можно отключить. В следующих разделах описаны некоторые различия между отладкой с процессом размещения и отладкой без него.

> [!NOTE]
> Начиная с Visual Studio 2017 параметр для отладки с использованием ведущего процесса больше не требуется и был удален. Дополнительные сведения см. в статье [Отладка. Среда Visual Studio 2017 призвана ускорить выполнение самого неприятного задания](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx).

## <a name="partial-trust-debugging-and-click-once-security"></a>Отладка с частичным доверием и модель безопасности Click-Once
 Отладка с частичным доверием требует наличия процесса размещения. Если отключить процесс размещения, отладка кода с частичным доверием не будет работать даже в случае, если на странице **Безопасность** окна **Свойства проекта** включена защита в случае частичного доверия. Дополнительные сведения см. в разделе [Практическое руководство. отладить приложение с частичным доверием](debugger-security.md).

## <a name="design-time-expression-evaluation"></a>Вычисление выражений в процессе разработки
 Для вычисления выражений во время разработки всегда используется процесс размещения. Отключение процесса размещения в окне **Свойства проекта** отключает вычисление выражений во время разработки для проектов библиотек классов. Для других типов проектов вычисление выражений во время разработки не отключается. При этом Visual Studio запускает реальный исполняемый файл и использует его для вычислений во время разработки в отсутствие процесса размещения. Из-за этого результаты могут быть разными.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Различия для AppDomain.CurrentDomain.FriendlyName
 `AppDomain.CurrentDomain.FriendlyName` возвращает различные результаты в зависимости от того, включен процесс размещения или нет. Если процесс размещения включен, вызов `AppDomain.CurrentDomain.FriendlyName` возвращает *имя_приложения*`.vhost.exe`. Если процесс размещения выключен, будет возвращено *имя_приложения*`.exe`.

## <a name="assemblygetcallingassemblyfullname-differences"></a>Различия для Assembly.GetCallingAssembly().FullName
 `Assembly.GetCallingAssembly().FullName` возвращает различные результаты в зависимости от того, включен процесс размещения или нет. Если процесс размещения включен, вызов `Assembly.GetCallingAssembly().FullName` возвращает `mscorlib`. При вызове `Assembly.GetCallingAssembly().FullName` с отключенным процессом размещения будет возвращено имя приложения.

## <a name="see-also"></a>См. также

- [Практическое руководство. Отладка не вполне надежного приложения](debugger-security.md)