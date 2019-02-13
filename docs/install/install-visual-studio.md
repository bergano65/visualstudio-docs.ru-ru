---
title: Установка Visual Studio
titleSuffix: ''
description: Сведения о поэтапной установке среды Visual Studio.
ms.date: 05/07/2018
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fab4a79bfd7a72b6b81493db241cd1ade8068158
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2019
ms.locfileid: "56156141"
---
# <a name="install-visual-studio-2017"></a>Установка Visual Studio 2017

Предлагаем ознакомиться с новым способом установки Visual Studio. В последней версии стало проще выбирать и устанавливать только нужные компоненты. Мы также сократили минимальные требования к месту на диске, поэтому установка Visual Studio выполняется еще быстрее и с меньшим влиянием на функционирование системы.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Установка Visual Studio для Mac](/visualstudio/mac/installation).

Хотите ознакомиться с другими новыми возможностями этой версии? Обратитесь к [заметкам о выпуске](/visualstudio/releasenotes/vs2017-relnotes).

Готовы к установке? Мы последовательно опишем каждое действие.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Шаг 1. Подготовка компьютера к установке Visual Studio

Перед началом установки Visual Studio:

1. Проверьте [требования к системе](/visualstudio/productinfo/vs2017-system-requirements-vs). Так вы узнаете, поддерживает ли ваш компьютер Visual Studio 2017.
2. Примените актуальные обновления Windows. Эти обновления гарантируют, что на компьютере установлены последние обновления для системы безопасности и необходимые системные компоненты для Visual Studio.
3. Перезагрузите систему. Перезагрузка гарантирует, что ожидающие установки или обновления компоненты не будут препятствовать установке Visual Studio.
4. Освободите место. Удалите ненужные файлы и приложения с системного диска. Например, запустите приложение очистки диска.

Сведения об использовании предыдущих версий Visual Studio параллельно с Visual Studio 2017 см. в разделе [Совместимость с предыдущими версиями](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Шаг 2.Скачивание Visual Studio

Теперь скачайте файл начального загрузчика Visual Studio. Для этого нажмите кнопку ниже, выберите нужный выпуск Visual Studio 2017, щелкните **Сохранить**, а затем **Открыть папку**.

 > [!div class="button"]
 > [Скачивание Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

## <a name="step-3---install-the-visual-studio-installer"></a>Шаг 3. Установка установщика Visual Studio

Теперь запустите файл начального загрузчика, чтобы установить Visual Studio Installer. Новый установщик имеет меньший размер и включает все необходимое для установки и настройки Visual Studio 2017.

1. В папке **Загрузки** дважды щелкните файл начального загрузчика, имя которого совпадает с именем одного из следующих файлов или похоже на них:

   * **vs_enterprise.exe** для Visual Studio Enterprise;
   * **vs_professional.exe** для Visual Studio Professional;
   * **vs_community.exe** для Visual Studio Community.  <br><br>

   Если появляется оповещение системы контроля учетных записей, нажмите кнопку **Да**.

2. Мы попросим вас принять [условия лицензии](https://visualstudio.microsoft.com/license-terms/) и [заявление о конфиденциальности](https://privacy.microsoft.com/privacystatement) корпорации Майкрософт. Нажмите кнопку **Продолжить**.

   ![Условия лицензии и заявление о конфиденциальности](media/vs2017-privacy-and-license-terms.PNG "Условия лицензии и заявление о конфиденциальности корпорации Майкрософт")

## <a name="step-4---select-workloads"></a>Шаг 4. Выбор рабочих нагрузок

Когда завершится установка программы установки, вы можете с ее помощью выбрать нужные наборы функций (рабочих нагрузок). Ниже описывается порядок действий.

1. Найдите нужную рабочую нагрузку на экране **Установка Visual Studio**.

   ![Выбор рабочей нагрузки в диалоговом окне программы установки Visual Studio 2017](../install/media/install-visual-studio-community.png)

     Например, выберите рабочую нагрузку "Разработка классических приложений .NET". В нее входит основной редактор кода по умолчанию, который предоставляет базовую поддержку редактирования кода для более чем 20 языков, возможность открывать и изменять код в любой папке без наличия проекта и интегрированное управление исходным кодом.

2. Выбрав нужные рабочие нагрузки, нажмите кнопку **Установить**.

    Далее будут отображаться экраны состояния, на которых демонстрируется ход установки Visual Studio.

3. После установки новых рабочих нагрузок и компонентов нажмите кнопку **Запуск**.

> [!TIP]
> В любой момент после установки можно установить рабочие нагрузки или компоненты, которые не были установлены изначально. Если среда Visual Studio открыта, выберите пункт **Сервис** > **Получить средства и компоненты...**; откроется Visual Studio Installer. **Visual Studio Installer** можно также открыть из меню "Пуск". Здесь можно выбрать рабочие нагрузки или компоненты, которые нужно установить, а затем нажать кнопку **Изменить**.

## <a name="step-5---select-individual-components-optional"></a>Шаг 5. Выбор отдельных компонентов (необязательно)

Если вы не хотите использовать функцию выбора рабочих нагрузок для настройки установки Visual Studio, можно установить отдельные компоненты. Чтобы выбрать отдельные компоненты, щелкните пункт **Отдельные компоненты** в Visual Studio Installer, выберите нужные компоненты и следуйте инструкциям.

  ![Visual Studio 2017 — установка отдельных компонентов](media/vs2017-components.PNG "Установка отдельных компонентов Visual Studio")

## <a name="step-6---install-language-packs-optional"></a>Шаг 6. Установка языковых пакетов (необязательно)

По умолчанию при первом запуске установщик пытается использовать язык операционной системы. Чтобы установить Visual Studio 2017 на нужном языке, выберите в установщике Visual Studio пункт **Языковые пакеты** и следуйте указаниям.

  ![Visual Studio 2017 — установка языковых пакетов](media/vs2017-languages.PNG "Установка языковых пакетов Visual Studio")

### <a name="change-the-installer-language-from-the-command-line"></a>Изменение языка установщика из командной строки

Язык по умолчанию можно изменить еще одним способом — запустив установщик из командной строки. Например, можно принудительно запустить установщик на английском языке, выполнив команду `vs_installer.exe --locale en-US`. Программа установки запомнит этот параметр и использует его при следующем запуске. Установщик поддерживает следующие токены языков: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru и tr-tr.

## <a name="step-7---change-the-installation-location-optional"></a>Шаг 7. Изменение расположения установки (дополнительно)

**Новая возможность в версии 15.7**. Теперь можно уменьшить место, занимаемое установкой Visual Studio на системном диске. Вы можете переместить кэш загрузки, общие компоненты, пакеты SDK и средства на другие диски и оставить Visual Studio на самом быстром диске.

  ![Visual Studio 2017 — изменение расположения установки](media/installation-options-by-location.png "Изменение расположения установки")

Дополнительные сведения см. на странице [Изменение расположения установки в Visual Studio](change-installation-locations.md).

## <a name="step-8---start-developing"></a>Шаг 8. Начало разработки

1. Когда установка Visual Studio завершится, нажмите кнопку **Запустить**, чтобы приступить к разработке в Visual Studio.

2. В меню **Файл** выберите команду **Создать проект**.

3. Выберите тип проекта.

   Например, чтобы [создать приложение C++](../ide/getting-started-with-cpp-in-visual-studio.md), нажмите **Установленные**, разверните узел **Visual C++**, а затем выберите тип проекта C++, который нужно создать.

   Чтобы [создать приложение C#](../get-started/csharp/tutorial-wpf.md), нажмите **Установленные**, разверните узел **Visual C#**, а затем выберите тип проекта C#, который нужно создать.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Обновление Visual Studio 2017](update-visual-studio.md)
* [Изменение Visual Studio 2017](modify-visual-studio.md)
* [Удаление Visual Studio 2017](uninstall-visual-studio.md)
* [Создание автономной установки Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Установка Visual Studio для Mac](/visualstudio/mac/installation)