---
title: "Установка Visual Studio 2017 | Документация Майкрософт"
description: "Сведения о поэтапной установке среды Visual Studio."
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
ms.assetid: 8d4297e4-9f43-4f12-95ec-22e61154480e
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 7adecc638a0ea4b198501752930a5c92c9db282c
ms.openlocfilehash: db6c415762bce85b2384358347310f93a056ec87
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="install-visual-studio-2017"></a>Установка Visual Studio 2017
Предлагаем ознакомиться с новым способом установки Visual Studio. В последней версии стало проще выбирать и устанавливать только нужные компоненты. Мы также сократили минимальные требования к месту на диске, поэтому установка Visual Studio выполняется еще быстрее и с меньшим влиянием на функционирование системы.

Хотите ознакомиться с другими новыми возможностями этой версии? Обратитесь к [заметкам о выпуске](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Готовы к установке? Мы последовательно опишем каждое действие.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Шаг 1. Подготовка компьютера к установке Visual Studio

Перед началом установки Visual Studio

1. Проверьте [требования к системе](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs). Так вы узнаете, поддерживает ли ваш компьютер Visual Studio 2017.
2. Примените актуальные обновления Windows. Эти обновления гарантируют, что на компьютере установлены последние обновления безопасности и необходимые системные компоненты для Visual Studio.
3. Перезагрузите систему. Перезагрузка гарантирует, что ожидающие установки или обновления компоненты не будут препятствовать установке Visual Studio.
4. Освободите место. Удалите ненужные файлы и приложения с системного диска. Например, запустите приложение очистки диска.

Сведения об использовании предыдущих версий Visual Studio параллельно с Visual Studio 2017 см. в разделе [Совместимость с предыдущими версиями](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Шаг 2.Скачивание Visual Studio

Теперь скачайте файл начального загрузчика Visual Studio. Для этого нажмите кнопку ниже, выберите нужный выпуск Visual Studio 2017, щелкните **Сохранить**, а затем **Открыть папку**.

 > [!div class="button"]
 > [Скачивание Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
<br/>

|         |         |
|---------|---------|
|  ![Значок пленки для видео](media/video-icon.png "Просмотреть видео")  |    [Посмотрите видео](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) о том, как скачать файл начального загрузчика Visual Studio и выбрать подходящий выпуск Visual Studio. |

## <a name="step-3---install-the-visual-studio-installer"></a>Шаг 3. Установка установщика Visual Studio

Теперь запустите файл начального загрузчика, чтобы установить Visual Studio Installer. Новый установщик имеет меньший размер и включает все необходимое для установки и настройки Visual Studio 2017.

1.  В папке **Загрузки** дважды щелкните файл начального загрузчика, имя которого совпадает с именем одного из следующих файлов или похоже на них:

  * **vs_enterprise.exe** для Visual Studio Enterprise;
  * **vs_professional.exe** для Visual Studio Professional;
  * **vs_community.exe** для Visual Studio Community.  <br><br>

  Если появляется оповещение системы контроля учетных записей, нажмите кнопку **Да**.

2.  Мы попросим вас принять [условия лицензии](https://www.visualstudio.com/license-terms/) и [заявление о конфиденциальности](https://go.microsoft.com/fwlink/?LinkID=824704) корпорации Майкрософт. Нажмите кнопку **Продолжить**.  

   ![Условия лицензии и заявление о конфиденциальности](media/vs2017-privacy-and-license-terms.PNG "Условия лицензии и заявление о конфиденциальности корпорации Майкрософт")

## <a name="step-4---select-workloads"></a>Шаг 4. Выбор рабочих нагрузок

Когда завершится установка программы установки, вы можете с ее помощью выбрать нужные наборы функций (рабочих нагрузок). Ниже описывается порядок действий.

1.  Найдите нужную рабочую нагрузку на экране **Установка Visual Studio**.

  ![Диалоговое окно установки Visual Studio 2017](media/vs2017-workloads.PNG "Установка рабочих нагрузок Visual Studio")

     Например, выберите рабочую нагрузку "Разработка классических приложений .NET". В нее входит основной редактор кода по умолчанию, который предоставляет базовую поддержку редактирования кода для более чем 20 языков, возможность открывать и изменять код в любой папке без наличия проекта и интегрированное управление исходным кодом.  

2.  Выбрав нужные рабочие нагрузки, нажмите кнопку **Установить**.

    Далее будут отображаться экраны состояния, на которых демонстрируется ход установки Visual Studio.

3.  После установки новых рабочих нагрузок и компонентов нажмите кнопку **Запуск**.

|         |         |
|---------|---------|
|  ![Значок пленки для видео](media/video-icon.png "Просмотреть видео")  |    [Посмотрите видео](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) о том, как установить Visual Studio Installer, а затем нужные рабочие нагрузки. |

## <a name="step-5---select-individual-components-optional"></a>Шаг 5. Выбор отдельных компонентов (необязательно)

Если вы не хотите использовать функцию выбора рабочих нагрузок для настройки установки Visual Studio, можно установить отдельные компоненты. Чтобы сделать это, щелкните **Отдельные компоненты** в Visual Studio Installer, выберите нужные элементы и следуйте инструкциям.

  ![Visual Studio 2017 — установка отдельных компонентов](media/vs2017-components.PNG "Установка отдельных компонентов Visual Studio")

  |         |         |
  |---------|---------|
  |  ![Значок пленки для видео](media/video-icon.png "Просмотреть видео")  |   [Посмотрите видео](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) об установке отдельных компонентов с помощью Visual Studio Installer. |

## <a name="step-6---install-language-packs-optional"></a>Шаг 6. Установка языковых пакетов (необязательно)

По умолчанию при первом запуске установщик пытается использовать язык операционной системы. Чтобы установить Visual Studio 2017 на нужном языке, выберите в установщике Visual Studio пункт **Языковые пакеты** и следуйте указаниям.

  ![Visual Studio 2017 — установка языковых пакетов](media/vs2017-languages.PNG "Установка языковых пакетов Visual Studio")

  |         |         |
  |---------|---------|
  |  ![Значок пленки для видео](media/video-icon.png "Просмотреть видео")  |   [Посмотрите видео](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) об установке языковых пакетов с помощью Visual Studio Installer. |

### <a name="change-the-installer-language-from-the-command-line"></a>Изменение языка установщика из командной строки

Язык по умолчанию можно изменить еще одним способом — запустив установщик из командной строки. Например, можно принудительно запустить установщик на английском языке, выполнив команду `vs_installer.exe --locale en-US`. Программа установки запомнит этот параметр и использует его при следующем запуске. Установщик поддерживает следующие токены языков: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru и tr-tr.

## <a name="step-7---launch-visual-studio"></a>Шаг 7. Запуск Visual Studio

Когда установка Visual Studio завершится, нажмите кнопку **Запустить**, чтобы [приступить к разработке в Visual Studio](../ide/get-started-developing-with-visual-studio.md).

## <a name="get-support"></a>Техническая поддержка

Иногда возникают проблемы. При сбое установки Visual Studio ознакомьтесь с советами, приведенными на странице [Устранение неполадок и исправление ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md).

## <a name="see-also"></a>См. также  
* [Изменение Visual Studio 2017](modify-visual-studio.md)
* [Обновление Visual Studio 2017](update-visual-studio.md)
* [Удаление Visual Studio 2017](uninstall-visual-studio.md)
* [Руководство администратора Visual Studio 2017](visual-studio-administrator-guide.md)
  * [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Как сообщить о проблеме с Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

