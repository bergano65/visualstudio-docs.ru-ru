---
title: "Установка инструментов R для Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ff60292-1b88-4ee9-b2b2-edd957f1a519
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 90b2481b0ec4f9387fe3a2c0b733a103e8c03845
ms.openlocfilehash: bc0b1112fe6f3acf2605101a863d831f41bb5f6d
ms.contentlocale: ru-ru
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-install-r-tools-for-visual-studio"></a>Порядок установки инструментов R для Visual Studio

Содержание раздела

- [Поддерживаемые версии Visual Studio](#supported-versions-of-visual-studio)
- [Установка RTVS в Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Установка RTVS в Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Автономная установка](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> После установки инструментов R может потребоваться настроить Visual Studio на использование макета, оптимизированного для обработки и анализа данных, как описано в разделе [Параметры](options.md#data-scientist-layout).

## <a name="supported-versions-of-visual-studio"></a>Поддерживаемые версии Visual Studio

Инструменты R для Visual Studio (RTVS) поддерживаются в выпусках Community, Professional и Enterprise [Visual Studio 2015 с обновлением 3 (или более поздней версии)](http://go.microsoft.com/fwlink/?LinkId=691129), а также [Visual Studio 2017](https://www.visualstudio.com/downloads/). 

Если имеется только оболочка Visual Studio, которая входит в состав других продуктов, таких как Visual Studio Test Professional и SQL Server Management Studio, то RTVS не устанавливаются. Это вызвано тем, что в оболочке Visual Studio отсутствуют необходимые компоненты для RTVS.


## <a name="installing-rtvs-in-visual-studio-2017"></a>Установка RTVS в Visual Studio 2017

> [!Important]
> Установка RTVS в Visual Studio 2017 на компьютере под управлением Windows 7 в настоящее время невозможна, как описано в статье об ошибке GitHub [№3561](https://github.com/Microsoft/RTVS/issues/3561). Данная проблема будет устранена в обновлении 15.3 для Visual Studio 2017.

1. Запустите установщик Visual Studio.
2. Выберите рабочую нагрузку **Приложения для обработки и анализа данных и аналитические приложения**.

    ![Рабочая нагрузка "Приложения для обработки и анализа данных и аналитические приложения" в Visual Studio 2017](~/docs/rtvs/media/installation-data-science-workload.png)

3. Настройте дополнительные параметры справа в разделе под тем же именем рабочей нагрузки. Обратите внимание, что по умолчанию эта рабочая нагрузка включает поддержку F # и Python. Для R необходимо как минимум выбрать компоненты **Поддержка языка R**, **Поддержка времени выполнения для средств разработки R** и **Microsoft R Client**.

RTVS устанавливается в каталог `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio` — где `<version>` обычно `2017`, а `<edition>` — `Community`, `Professional` или `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Установка RTVS в Visual Studio 2015

Если используется Visual Studio 2015, интерпретатор R и инструменты R необходимо установить отдельно.

### <a name="install-an-r-interpreter"></a>Установка интерпретатора R

Для RTVS требуется 64-разрядная установка R версии 3.2.1 или более поздней из одного или нескольких следующих источников.

* [Microsoft R Open](https://mran.microsoft.com/download/)
* [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
* [CRAN R](https://cran.r-project.org/bin/windows/base/)

Для Microsoft R Open и CRAN R возможны установка и использование нескольких версий. Однако Microsoft R Client поддерживает только одну версию и всегда будет использовать последнюю из версий, которые установлены на компьютере.

### <a name="install-the-r-tools"></a>Установка инструментов R

Скачайте актуальную версию RTVS с сайта [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). RTVS проверит наличие подходящей версии Visual Studio и поможет установить интерпретатор R, если он еще не установлен.

RTVS устанавливается в каталог `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Автономная установка Visual Studio и RTVS

Вариант автономной установки подходит для компьютеров, которые не подключены к Интернету.

1. Следуйте инструкциям по созданию автономного установщика для вашей версии Visual Studio. 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Установите Visual Studio с помощью автономного установщика.
1. [Скачайте RTVS](https://aka.ms/rtvs-current) и установите их в обычном режиме.

## <a name="see-also"></a>См. также

- [Начало работы с R](getting-started-with-r.md)
- [Инструменты R. Примеры проектов](getting-started-samples.md)
- [Получение справки](getting-started-help.md)
- [Настройки параметров](options.md)

