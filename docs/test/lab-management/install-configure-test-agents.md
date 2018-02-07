---
title: "Установка и настройка агентов тестирования | Документы Майкрософт"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configure test agents, test lab
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5caa566e15f7f3c4c69f8d33a6c7dd0eead38785
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="install-and-configure-test-agents"></a>Установка и настройка агентов тестирования

Для сценариев тестирования с использованием Visual Studio и Visual Studio Team Services или Team Foundation Server (TFS) не требуется контроллер тестирования, так как Agents для Microsoft Visual Studio обрабатывает оркестрацию путем взаимодействия с Team Services или TFS. Например, вы выполняете непрерывные тесты с рабочими процессами сборки и выпуска в Team Services или TFS.

Если вам нужно, чтобы агент или контроллер тестирования работал с TFS 2013, используйте обновление 5 для Agents для Microsoft Visual Studio 2013 и настройте контроллер тестирования.

Также рассмотрите, будет ли проще использовать [вместо этого управление сборками и выпусками](use-build-or-rm-instead-of-lab-management.md).

## <a name="what-do-i-need"></a>Что мне нужно делать?

**Где получить контроллер тестирования и агенты тестирования?**

* Если вы выполняете тесты с помощью задач vNext сборки и хотите установить агенты из локального каталога: 

  * [Скачайте Agents для Microsoft Visual Studio 2015 RTM и обновление 1](http://go.microsoft.com/fwlink/p/?LinkId=619266). 

  * [Скачайте Agents для Microsoft Visual Studio 2017 и обновление 2 для Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs): выберите **Инструменты для Visual Studio 2015** и затем **Agents для Visual Studio 2015** в левой панели навигации.

* [Скачайте обновление 5 для Agents для Microsoft Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=619264), если хотите запустить следующее:

  * Нагрузочные тесты с использованием удаленных локальных компьютеров.

  * Непрерывные тесты в удаленном режиме с использованием Microsoft Test Manager или MSTest и параметров теста для лабораторных сред.

  * Непрерывные тесты с использованием TFS 2013.

Эти установщики доступны в виде ISO-файлов (виртуальный компакт-диск), что упрощает установку на виртуальных машинах. 

[Можно ли комбинировать версии TFS, Microsoft Test Manager, контроллера тестирования и агента тестирования?](#MixedVersions)

**Какие требования к системе предъявляются для установки контроллера тестирования и агентов тестирования?**

| Элемент | Требования |
| ---- | ------------ |
| **Агент** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 с пакетом обновления 1 (SP1)<br />Windows XP с пакетом обновления 3 (SP3)<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008, выпуск 2 с пакетом обновления 1 |
| **Контроллер** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 с пакетом обновления 1 (SP1)<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008, выпуск 2 с пакетом обновления 1 |
| **.NET Framework** | .NET Framework 4,5 |

## <a name="q--a"></a>Вопросы и ответы

<!-- BEGINSECTION class="m-qanda" -->

<a name="MixedVersions"></a>

####<a name="q-can-i-mix-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Вопрос. Можно ли комбинировать версии TFS, Microsoft Test Manager, контроллера тестирования и агента тестирования?

Ответ. Да, ниже указаны совместимые и поддерживаемые сочетания:

| TFS | Microsoft Test Manager с Lab Center | Контроллер | Агент |
| --- | -------------------------------------- | ---------- | ----- |
| 2015: обновление с 2013 | 2013 | 2013 |2013 |
| 2015: новая установка | 2013 | 2013 | 2013 |
| 2015: обновление с 2013 или новая установка | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

####<a name="q-will-the-test-agent-2015-support-all-the-scenarios-supported-by-test-controller-and-test-agent-of-visual-studio-2013"></a>Вопрос. Будет ли агент тестирования 2015 поддерживать все сценарии, поддерживаемые контроллером тестирования и агентом тестирования в Visual Studio 2013?

Ответ. Мы рекомендуем использовать Agents для Visual Studio во всех сценариях нового автоматического тестирования. Вы можете использовать задачу "Deploy Test Agents" (Развертывание агентов тестирования) в определении сборки, чтобы скачать и установить агенты тестирования на компьютере.
В следующей таблице описаны сценарии, поддерживаемые Agents для Visual Studio 2013 и альтернативными решениями для Team Foundation Server (TFS) 2015 и Team Services (TS).

| Сценарии, поддерживаемые Agents для Visual Studio 2013 | Альтернатива в TFS и TS |
| --- | --- |
| Рабочий процесс "сборка-развертывание-тестирование" в Visual Studio | Пользователи могут использовать [определение сборки](https://www.visualstudio.com/team-services/continuous-integration/) (не сборку XAML) для сценариев сборки, развертывания и тестирования в TFS. |
| Нагрузочные тесты (тестирование производительности) с использованием удаленных локальных компьютеров | Используйте обновление 5 для контроллеров/агентов тестирования 2013 для локального выполнения нагрузочных тестов. [Дополнительные сведения](https://msdn.microsoft.com/library/ff400223.aspx). |
| Удаленное выполнение автоматических тестов из Microsoft Test с использованием лабораторной среды | Сейчас альтернативы этому сценарию не существует. Мы рекомендуем использовать задачу "Запуск функциональных тестов" в определениях сборок и выпусков (не в сборке XAML) для удаленного выполнения тестов. |
| Разработчики, выполняющие удаленные тесты в Visual Studio | Больше не поддерживается. |

<!-- ENDSECTION -->

## <a name="see-also"></a>См. также

* [Настройка компьютеров и сбор диагностических данных с помощью параметров тестирования](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)
