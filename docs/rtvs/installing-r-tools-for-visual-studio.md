---
title: Установка инструментов R
description: Инструкции по установке инструментов R в Visual Studio 2017 и Visual Studio 2015, в том числе по автономной установке.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 0bede3afc12eb7f22f516d7f21727609d5724a9a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943159"
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

Инструменты R для Visual Studio (RTVS) поддерживаются в выпусках Windows Community (бесплатный), Professional и Enterprise как [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), так и [Visual Studio 2015 с обновлением 3 (или более поздней версии)](http://go.microsoft.com/fwlink/?LinkId=691129) (прямое скачивание).

Инструменты RTVS в настоящее время не поддерживаются в Visual Studio для Mac.

Если имеется только оболочка Visual Studio Shell, которая входит в состав таких продуктов, как Visual Studio Test Professional и SQL Server Management Studio, то RTVS не устанавливаются. В оболочке Visual Studio Shell отсутствуют необходимые компоненты для RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Установка RTVS в Visual Studio 2017

1. Запустите установщик Visual Studio и выберите вариант **Изменить** (подробные сведения см. в разделе [Изменение Visual Studio](../install/modify-visual-studio.md)). Если вы еще не установили Visual Studio, см. раздел [Установка Visual Studio](../install/install-visual-studio.md). В Windows 7 убедитесь, что в установщике отображается Visual Studio 2017 *версии 15.2 сборки 26430.12* или более поздней версии.

1. Выберите рабочую нагрузку **Приложения для обработки и анализа данных и аналитические приложения**.

    ![Рабочая нагрузка "Приложения для обработки и анализа данных и аналитические приложения" в Visual Studio 2017](media/installation-data-science-workload.png)

1. Настройте дополнительные параметры справа в разделе под тем же именем рабочей нагрузки. По умолчанию эта рабочая нагрузка включает поддержку F# и Python. Для R нужно выбрать по меньшей мере компоненты **Поддержка языка R**, **Поддержка времени выполнения для средств разработки R** и **Microsoft R Client**.

RTVS устанавливается в папке *%ProgramFiles(x86)%\Microsoft Visual Studio\<версия>\<выпуск>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio*, где *\<версия>* обычно `2017`, а *\<выпуск>*  — `Community`, `Professional` или `Enterprise`.

## <a name="install-rtvs-in-visual-studio-2015"></a>Установка RTVS в Visual Studio 2015

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

1. Перейдите в раздел [Создание автономной установки Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Если вы используете Visual Studio 2015, выберите **2015** в селекторе над содержанием.

1. Ознакомьтесь с инструкциями по созданию автономной установки на веб-странице.

1. Для Visual Studio 2015 скачайте автономные установщики RTVS со страниц [https://aka.ms/rtvs-current-zip](https://aka.ms/rtvs-current-zip) и [https://aka.ms/rtvs-remote-zip](https://aka.ms/rtvs-remote-zip).

1. Установите Visual Studio и RTVS с помощью автономных установщиков.

## <a name="see-also"></a>См. также

- [Начало работы с R](getting-started-with-r.md)
- [Инструменты R. Примеры проектов](getting-started-samples.md)
- [Справка в инструментах R](getting-started-help.md)
- [Параметры инструментов R](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (прежнее название — R Server)](/machine-learning-server/)