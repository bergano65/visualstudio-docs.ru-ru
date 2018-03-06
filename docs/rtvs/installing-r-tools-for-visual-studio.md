---
title: "Установка инструментов R для Visual Studio | Документация Майкрософт"
description: "Узнайте, как установить Инструменты R для Visual Studio 2017 и Visual Studio 2015, в том числе автономная установка."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
dev_langs:
- R
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 76dc2623edebed6cca48c40c0ad0bc96f783e39d
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Порядок установки инструментов R для Visual Studio

Содержание этой статьи

- [Поддерживаемые версии Visual Studio](#supported-versions-of-visual-studio)
- [Установка RTVS в Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Установка RTVS в Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Автономная установка](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> После установки инструментов R может потребоваться настроить Visual Studio на использование макета, оптимизированного для обработки и анализа данных, как описано в [этой статье](options-for-r-tools-in-visual-studio.md).

## <a name="supported-versions-of-visual-studio"></a>Поддерживаемые версии Visual Studio

Инструменты R для Visual Studio (RTVS) поддерживаются в выпусках Windows Community (бесплатный), Professional и Enterprise как [Visual Studio 2017](https://www.visualstudio.com/downloads/), так и [Visual Studio 2015 с обновлением 3 (или более поздней версии)](http://go.microsoft.com/fwlink/?LinkId=691129) (прямое скачивание).

Инструменты RTVS в настоящее время не поддерживаются в Visual Studio для Mac.

Если имеется только оболочка Visual Studio Shell, которая входит в состав таких продуктов, как Visual Studio Test Professional и SQL Server Management Studio, то RTVS не устанавливаются. В оболочке Visual Studio Shell отсутствуют необходимые компоненты для RTVS.

## <a name="installing-rtvs-in-visual-studio-2017"></a>Установка RTVS в Visual Studio 2017

1. Запустите установщик Visual Studio. (См. раздел [Скачивание](https://www.visualstudio.com/downloads/), если вы еще не установили Visual Studio.) В Windows 7 убедитесь, что в установщике отображается Visual Studio 2017 *версии 15.2 сборки 26430.12* или более поздней версии.

1. Выберите рабочую нагрузку **Приложения для обработки и анализа данных и аналитические приложения**.

    ![Рабочая нагрузка "Приложения для обработки и анализа данных и аналитические приложения" в Visual Studio 2017](media/installation-data-science-workload.png)

1. Настройте дополнительные параметры справа в разделе под тем же именем рабочей нагрузки. По умолчанию эта рабочая нагрузка включает поддержку F # и Python. Для R нужно выбрать по меньшей мере компоненты **Поддержка языка R**, **Поддержка времени выполнения для средств разработки R** и **Microsoft R Client**.

RTVS устанавливается в каталог `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio` — где `<version>` обычно `2017`, а `<edition>` — `Community`, `Professional` или `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Установка RTVS в Visual Studio 2015

Если используется Visual Studio 2015, интерпретатор R и инструменты R необходимо установить отдельно.

### <a name="install-an-r-interpreter"></a>Установка интерпретатора R

Для RTVS требуется 64-разрядная установка R версии 3.2.1 или более поздней из одного или нескольких следующих источников.

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Для Microsoft R Open и CRAN R возможны установка и использование нескольких версий. Однако Microsoft R Client поддерживает только одну версию и всегда использует последнюю из версий, которые установлены на компьютере.

### <a name="install-the-r-tools"></a>Установка инструментов R

Скачайте актуальную версию RTVS для Visual Studio 2015 с сайта [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). RTVS проверяют наличие подходящей версии Visual Studio и помогают установить интерпретатор R, если он еще не установлен.

> [!Note]
> Автономный установщик RTVS работает только с Visual Studio 2015. Для Visual Studio 2017 установите поддержку R в составе [рабочей нагрузки "Приложения для обработки и анализа данных и аналитические приложения"](#installing-rtvs-in-visual-studio-2017), как описано выше.

Инструменты RTVS для Visual Studio 2015 устанавливаются в папке `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Автономная установка Visual Studio и RTVS

Вариант автономной установки подходит для компьютеров, которые не подключены к Интернету.

1. Следуйте инструкциям по созданию автономного установщика для вашей версии Visual Studio:

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Для Visual Studio 2015 скачайте автономные установщики RTVS: [https://aka.ms/rtvs-current-zip](https://aka.ms/rtvs-current-zip) и [https://aka.ms/rtvs-remote-zip](https://aka.ms/rtvs-remote-zip).

1. Установите Visual Studio и RTVS с помощью автономных установщиков.

## <a name="see-also"></a>См. также

- [Начало работы с R](getting-started-with-r.md)
- [Инструменты R. Примеры проектов](getting-started-samples.md)
- [Получение справки](getting-started-help.md)
- [Настройки параметров](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (прежнее название — R Server)](/machine-learning-server/)