---
title: Как выполнить Устранение неполадок при обновлениях неудачных проекта | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 2e21feda11ef4d3405fa1488740fefe7c7238dc5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942022"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Как выполнить Устранение неполадок с неудачными обновлениями Visual Studio проекта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Иногда Visual Studio не удается полностью преобразовать проект, созданный в более ранней версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Если советы в следующих разделах не решат свою проблему, можно найти дополнительные сведения о TechNet [вики-сайте: Портал разработки](http://go.microsoft.com/fwlink/?LinkId=254808).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Проект не запускается, поскольку не удалось найти файлы
 Файл проекта содержит жестко заданные пути к файлам, которые используются в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для запуска проекта при нажатии клавиши F5. В числе этих путей может быть расположение файла devenv.exe и других обязательных файлов. В обновленной версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] пути к этим файлам могут быть изменены.

#### <a name="to-resolve-incorrect-file-paths"></a>Исправление неправильных путей

1.  Откройте файл проекта в текстовом редакторе.

2.  Внимательно проверьте наличие неправильных путей к файлам, особенно тех, которые содержат номер версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

3.  Измените неправильные пути к файлам, чтобы они указывали на новые конечные объекты.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Построение проекта не запускается, поскольку ссылки недопустимы
 При обновлении [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], возможно, также выполняется обновление версии [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Если проект содержит ссылки, не используемые в более новой версии [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], они могут не разрешаться правильно. Это особенно вероятно для ссылок, включающих номера версий, например `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Если код содержит много недопустимых ссылок, простейшим решением может стать применение функции настройки для различных сред [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] с целью настройки на более раннюю версию [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="to-resolve-incorrect-references"></a>Разрешение неверных ссылок

1. Откройте файл проекта в текстовом редакторе.

2. Откройте свойства проекта.

3. Выделите верное значение для параметра **Целевая рабочая среда**. Также можно изменить значение элемента `<TargetFrameworkVersion>` непосредственно в файле проекта.

   Если вы хотите, чтобы проект выполнялся в обновленной версии [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], необходимо обновить ссылки проекта, а также любые операторы `Imports` или `Using`, вызывающие эти ссылки. Если проект загружается в интегрированной среде разработки, можно обновить ссылки с помощью **Обозревателя решений** или **Диспетчера ссылок**.

## <a name="see-also"></a>См. также раздел
 [Или обновления (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [преобразование в ASP.NET 4](http://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
