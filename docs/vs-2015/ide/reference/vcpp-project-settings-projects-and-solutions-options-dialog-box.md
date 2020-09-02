---
title: Параметры проекта VC++, страница "Проекты и решения", диалоговое окно "Параметры" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef861d13387c013659e5e4c1714680b71896858c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657867"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Параметры проекта VC++, страница "Проекты и решения", диалоговое окно "Параметры"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В этом диалоговом окне можно определять параметры проекта [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], связанные с файлами журналов сборки и другими вспомогательными файлами.

### <a name="to-access-this-dialog-box"></a>Вызов диалогового окна

1. В меню **Сервис** выберите команду **Параметры**.

2. Выберите **Проекты и решения**, а затем **Параметры проекта VC++** .

## <a name="build-customization-search-path"></a>Путь поиска настройки сборки
 Задает список каталогов, содержащих файлы с расширением Rules, которые определяют правила сборки проектов.

## <a name="build-logging"></a>Журнал сборки
 **Да** Включает создание файла журнала сборки. Этот параметр создает файл BuildLog.htm в каталоге временных файлов проекта. После каждой новой сборки файл BuildLog.htm перезаписывается.

 **Нет** Отключает создание файла журнала сборки.

## <a name="build-timing"></a>Время сборки
 **Да** Включает синхронизацию времени сборки. Если этот параметр выбран, время, затрачиваемое на выполнение сборки, отображается в окне вывода. Дополнительные сведения см. в разделе [Окно вывода](../../ide/reference/output-window.md).

 **Нет** Отключает синхронизацию времени сборки.

## <a name="extensions-to-hide"></a>Скрываемые расширения
 Задает расширения файлов, которые не будут отображаться в **обозревателе решений** при выборе параметра **Показать все файлы**.

## <a name="extensions-to-include"></a>Включаемые расширения
 Задает расширения файлов, которые могут переноситься в проект.

## <a name="maximum-concurrent-c-compilations"></a>Максимум одновременных компиляций C++
 Задает максимальное число ядер ЦП для параллельной компиляции C++.

## <a name="show-environment-in-log"></a>Отображать среду в журнале
 **Да** Содержит список переменных среды в файле журнала сборки. Этот параметр задает вывод всех переменных среды во время сборки проектов [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] в файл журнала сборки.

 **Нет** Исключите переменные среды из файла журнала сборки.

## <a name="solution-explorer-mode"></a>Режим обозревателя решений
 **Показывать только файлы в проекте** Настраивает **Обозреватель решений** для вывода в проект только файлов.

 **Отобразить все файлы** Настраивает **Обозреватель решений** для отображения файлов проекта и файлов на диске в папке проекта.

## <a name="see-also"></a>См. также:
 [Разработка программ на c/c++](https://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008) [Сборка справочника по c/c++](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
