---
title: "Установка поддержки Python в Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce3d3656-7ba2-490d-92df-0bb3e3badf92
caps.latest.revision: 11
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
translationtype: Human Translation
ms.sourcegitcommit: e9a05d008f671fb79d6813a14c594b82f27697e3
ms.openlocfilehash: e0a51155a42fb51244114da86a292381a7a28a21
ms.lasthandoff: 03/27/2017

---

# <a name="installing-python-support-for-visual-studio"></a>Установка поддержки Python для Visual Studio

Чтобы установить поддержку Python для Visual Studio, выполните инструкции из раздела, который соответствует вашей версии Visual Studio.

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 и более ранние версии](#visual-studio-2013-and-earlier)

Обратите внимание, что для Visual Studio 2015 и более ранних версий необходимо отдельно установить любой интерпретатор Python на ваш выбор. Дополнительные сведения см. в статье [Среды Python](python-environments.md).

Чтобы быстро проверить поддержку Python после установки, откройте интерактивное окно Python. Для этого нажмите клавиши Alt + I и введите `2+2`. Если вы не увидите результат `4`, проверьте выполненные действия.

> [!Tip]
> Рабочая нагрузка Python содержит полезное расширение Cookiecutter, которое предоставляет графический пользовательский интерфейс для поиска шаблонов, ввода параметров шаблонов и создания проектов и файлов. Дополнительные сведения см. в статье [Использование расширения Cookiecutter](cookiecutter.md).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Установите ["Visual Studio 2017 Preview" со страницы https://www.visualstudio.com/vs/preview](https://www.visualstudio.com/vs/preview). **Примечание**. Этот канал предварительной версии *отличается* от итоговой версии Visual Studio 2017 и содержит функции, которые находятся на этапе разработки и появятся в дальнейших обновлениях Visual Studio 2017, включая поддержку Python.

1. В установщике предварительной версии выберите рабочую нагрузку **Web & Cloud > Python Development** (Облачная и веб-разработка > Разработка Python).

    ![Рабочая нагрузка разработки Python в установщике Visual Studio](media/installation-python-workload.png)

1. В правой части окна установщика выберите интерпретатор Python и все дополнительные средства, которые вам нужны. Например, если планируется разработать расширения C++ для Python, включите параметр **Собственные средства разработки Python**.

    ![Параметры разработки Python в установщике Visual Studio](media/installation-python-options.png)

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Чтобы запустить установщик Visual Studio, откройте **Панель управления > Программы и компоненты**, затем выберите **Microsoft Visual Studio 2015** и нажмите кнопку **Изменить**.

1. В самом установщике выберите действие **Изменить**.

1. Выберите **Языки программирования > Инструменты Python для Visual Studio** и нажмите **Далее**:

    ![Выбор PTVS в установщике Visual Studio 2015](media/installation-vs2015.png)    

1. Когда завершится работа установщика Visual Studio, [установите любой интерпретатор Python на свой выбор](python-environments.md#selecting-and-installing-python-interpreters).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 и более ранние версии

1. Установите версию Инструментов Python для Visual Studio, соответствующую вашей версии Visual Studio.

    - Visual Studio 2013: [PTVS 2.2 для Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). В Visual Studio 2013 этот процесс можно запустить через диалоговое окно **Файл > Новый проект** в Visual Studio.
    - Visual Studio 2012: [PTVS 2.1 для Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 для Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Selecting and installing Python interpreters](python-environments.md#selecting-and-installing-python-interpreters) (Установка и настройка интерпретаторов Python).

## <a name="install-locations"></a>Расположения установки

По умолчанию поддержка Python устанавливается для всех пользователей на компьютере.

В Visual Studio 2017 рабочая нагрузка Python устанавливается в каталог `%ProgramFiles(x86)%\Microsoft Visual Studio\Preview\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`, где &lt;VS_edition&gt; может иметь значение Community, Professional или Enterprise.

В Visual Studio 2015 и более ранних версиях используются такие пути установки:

- 32-разрядная версия.
  - Путь: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Расположение пути в реестре: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64-разрядная версия.
  - Путь: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Расположение пути в реестре: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

где:

- &lt;VS_ver&gt; принимает одно из этих значений:    
    - 14.0 for Visual Studio 2015
    - 12.0 for Visual Studio 2013
    - 11.0 for Visual Studio 2012
    - 10.0 for Visual Studio 2010
- &lt;PTVS_ver&gt; — это номер версии, например 2.2, 2.1, 2.0, 1.1, 1.5 или 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Пользовательские установки (для версии 1.5 и более ранних)

Средства Python для Visual Studio 1.5 и более ранних версий можно установить только для текущего пользователя. Путь установки будет выглядеть так: `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>` Здесь &lt;VS_ver&gt; и &lt;PTVS_ver&gt; имеют то же значение, которое описано выше.

