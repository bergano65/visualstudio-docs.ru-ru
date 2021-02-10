---
title: Установка инструментов R
description: Инструкции по установке инструментов R в Visual Studio 2017 и Visual Studio 2015, в том числе по автономной установке.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: fa5346d65a94646a0fa5e922f3b0055d8cdb6c0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908652"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Порядок установки инструментов R для Visual Studio

Содержание этой статьи

- [Поддерживаемые версии Visual Studio](#supported-versions-of-visual-studio)
- [Установка RTVS в Visual Studio 2017](#install-rtvs-in-visual-studio-2017)
- [Установка RTVS в Visual Studio 2015](#install-rtvs-in-visual-studio-2015)
- [Автономная установка](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> После установки инструментов R может потребоваться настроить Visual Studio на использование макета, оптимизированного для обработки и анализа данных, как описано в [этой статье](options-for-r-tools-in-visual-studio.md).

## <a name="supported-versions-of-visual-studio"></a>Поддерживаемые версии Visual Studio

Инструменты R для Visual Studio (RTVS) поддерживаются в выпусках Windows Community (бесплатный), Professional и Enterprise как [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), так и [Visual Studio 2015 с обновлением 3 (или более поздней версии)](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) (прямое скачивание).

Инструменты RTVS в настоящее время не поддерживаются в Visual Studio для Mac.

Если имеется только оболочка Visual Studio Shell, которая входит в состав таких продуктов, как Visual Studio Test Professional и SQL Server Management Studio, то RTVS не устанавливаются. В оболочке Visual Studio Shell отсутствуют необходимые компоненты для RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Установка RTVS в Visual Studio 2017

1. Запустите установщик Visual Studio и выберите вариант **Изменить** (подробные сведения см. в разделе [Изменение Visual Studio](../install/modify-visual-studio.md)). Если вы еще не установили Visual Studio, см. раздел [Установка Visual Studio](../install/install-visual-studio.md). В Windows 7 убедитесь, что в установщике отображается Visual Studio 2017 *версии 15.2 сборки 26430.12* или более поздней версии.

1. Выберите рабочую нагрузку **Приложения для обработки и анализа данных и аналитические приложения**.

    ![Рабочая нагрузка "Приложения для обработки и анализа данных и аналитические приложения" в Visual Studio 2017](media/installation-data-science-workload.png)

1. Настройте дополнительные параметры справа в разделе под тем же именем рабочей нагрузки. По умолчанию эта рабочая нагрузка включает поддержку F# и Python. Для R нужно выбрать по меньшей мере компоненты **Поддержка языка R**, **Поддержка времени выполнения для средств разработки R** и **Microsoft R Client**.

RTVS устанавливается в папке *%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio*, где *\<version>* обычно `2017`, а *\<edition>*  — `Community`, `Professional` или `Enterprise`.

## <a name="install-rtvs-in-visual-studio-2015"></a>Установка RTVS в Visual Studio 2015

Если используется Visual Studio 2015, интерпретатор R и инструменты R необходимо установить отдельно.

### <a name="install-an-r-interpreter"></a>Установка интерпретатора R

Для RTVS требуется 64-разрядная установка R версии 3.2.1 или более поздней из одного или нескольких следующих источников.

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Для Microsoft R Open и CRAN R возможны установка и использование нескольких версий. Однако Microsoft R Client поддерживает только одну версию и всегда использует последнюю из версий, которые установлены на компьютере.

### <a name="install-the-r-tools"></a>Установка инструментов R

Скачайте актуальную версию RTVS для Visual Studio 2015 с сайта [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe). RTVS проверяют наличие подходящей версии Visual Studio и помогают установить интерпретатор R, если он еще не установлен.

> [!Note]
> Автономный установщик RTVS работает только с Visual Studio 2015. Для Visual Studio 2017 установите поддержку R в составе [рабочей нагрузки "Приложения для обработки и анализа данных и аналитические приложения"](#install-rtvs-in-visual-studio-2017), как описано выше.

Инструменты RTVS для Visual Studio 2015 устанавливаются в папке `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Автономная установка Visual Studio и RTVS

Вариант автономной установки подходит для компьютеров, которые не подключены к Интернету.

1. Перейдите в раздел [Создание автономной установки Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Если вы используете Visual Studio 2015, выберите **2015** в селекторе над содержанием.

1. Ознакомьтесь с инструкциями по созданию автономной установки на веб-странице.

1. Для Visual Studio 2015 скачайте автономные установщики RTVS со страниц [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) и [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip).

1. Установите Visual Studio и RTVS с помощью автономных установщиков.

## <a name="see-also"></a>См. также

- [Начало работы с R](getting-started-with-r.md)
- [Инструменты R. Примеры проектов](getting-started-samples.md)
- [Справка в инструментах R](getting-started-help.md)
- [Параметры инструментов R](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (прежнее название — R Server)](/machine-learning-server/)
