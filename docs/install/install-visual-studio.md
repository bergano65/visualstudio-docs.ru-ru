---
title: Установка Visual Studio 2017 | Документация Майкрософт
description: Сведения о поэтапной установке среды Visual Studio.
ms.custom: ''
ms.date: 12/04/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3f6acdd338b0ae8d23fba338c8564d2bd95ad45
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2018
---
# <a name="install-visual-studio-2017"></a>Установка Visual Studio 2017
Предлагаем ознакомиться с новым способом установки Visual Studio. В последней версии стало проще выбирать и устанавливать только нужные компоненты. Мы также сократили минимальные требования к месту на диске, поэтому установка Visual Studio выполняется еще быстрее и с меньшим влиянием на функционирование системы.

Хотите ознакомиться с другими новыми возможностями этой версии? Обратитесь к [заметкам о выпуске](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Готовы к установке? Мы последовательно опишем каждое действие.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Шаг 1. Подготовка компьютера к установке Visual Studio

Перед началом установки Visual Studio:

1. Проверьте [требования к системе](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs). Так вы узнаете, поддерживает ли ваш компьютер Visual Studio 2017.
2. Примените актуальные обновления Windows. Эти обновления гарантируют, что на компьютере установлены последние обновления для системы безопасности и необходимые системные компоненты для Visual Studio.
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
|  ![значок кинокамеры для видео](media/video-icon.png "Просмотреть видео")  |    [Посмотрите видео](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) о том, как скачать файл начального загрузчика Visual Studio и выбрать подходящий выпуск Visual Studio. |

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

 ![Выбор рабочей нагрузки в диалоговом окне программы установки Visual Studio 2017](../install/media/install-visual-studio-enterprise.png)

     Например, выберите рабочую нагрузку "Разработка классических приложений .NET". В нее входит основной редактор кода по умолчанию, который предоставляет базовую поддержку редактирования кода для более чем 20 языков, возможность открывать и изменять код в любой папке без наличия проекта и интегрированное управление исходным кодом.  

2.  Выбрав нужные рабочие нагрузки, нажмите кнопку **Установить**.

    Далее будут отображаться экраны состояния, на которых демонстрируется ход установки Visual Studio.

3.  После установки новых рабочих нагрузок и компонентов нажмите кнопку **Запуск**.  

> [!TIP]
>  В любой момент после установки можно установить рабочие нагрузки или компоненты, которые не были установлены изначально. Если среда Visual Studio открыта, выберите пункт **Сервис** > **Получить средства и компоненты...**; откроется Visual Studio Installer. **Visual Studio Installer** можно также открыть из меню "Пуск". Здесь можно выбрать рабочие нагрузки или компоненты, которые нужно установить, а затем нажать кнопку **Изменить**.  

|         |         |
|---------|---------|
|  ![значок кинокамеры для видео](media/video-icon.png "Просмотреть видео")  |    [Посмотрите видео](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) о том, как установить Visual Studio Installer, а затем нужные рабочие нагрузки. |

## <a name="step-5---select-individual-components-optional"></a>Шаг 5. Выбор отдельных компонентов (необязательно)

Если вы не хотите использовать функцию выбора рабочих нагрузок для настройки установки Visual Studio, можно установить отдельные компоненты. Чтобы выбрать отдельные компоненты, щелкните пункт **Отдельные компоненты** в Visual Studio Installer, выберите нужные компоненты и следуйте инструкциям.

  ![Visual Studio 2017 — установка отдельных компонентов](media/vs2017-components.PNG "Установка отдельных компонентов Visual Studio")

  |         |         |
  |---------|---------|
  |  ![значок кинокамеры для видео](media/video-icon.png "Просмотреть видео")  |   [Посмотрите видео](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) об установке отдельных компонентов с помощью Visual Studio Installer. |

## <a name="step-6---install-language-packs-optional"></a>Шаг 6. Установка языковых пакетов (необязательно)

По умолчанию при первом запуске установщик пытается использовать язык операционной системы. Чтобы установить Visual Studio 2017 на нужном языке, выберите в установщике Visual Studio пункт **Языковые пакеты** и следуйте указаниям.

  ![Visual Studio 2017 — установка языковых пакетов](media/vs2017-languages.PNG "Установка языковых пакетов Visual Studio")

  |         |         |
  |---------|---------|
  |  ![значок кинокамеры для видео](media/video-icon.png "Просмотреть видео")  |   [Посмотрите видео](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) об установке языковых пакетов с помощью Visual Studio Installer. |

### <a name="change-the-installer-language-from-the-command-line"></a>Изменение языка установщика из командной строки

Язык по умолчанию можно изменить еще одним способом — запустив установщик из командной строки. Например, можно принудительно запустить установщик на английском языке, выполнив команду `vs_installer.exe --locale en-US`. Программа установки запомнит этот параметр и использует его при следующем запуске. Установщик поддерживает следующие токены языков: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru и tr-tr.


## <a name="step-7---start-developing"></a>Шаг 7. Начало разработки
1. Когда установка Visual Studio завершится, нажмите кнопку **Запустить**, чтобы [приступить к разработке в Visual Studio](../ide/get-started-developing-with-visual-studio.md).

2. В меню **Файл** выберите команду **Создать проект**.

3. Выберите тип проекта. <br><br>
   Например, чтобы [создать приложение C++](../ide/getting-started-with-cpp-in-visual-studio.md), щелкните **Установленные**, разверните узел **Visual C++**, а затем выберите тип проекта C++, который нужно создать. <br><br>
   Чтобы [создать приложение C#](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md), щелкните **Установленные**, разверните узел **Visual C#**, а затем выберите тип проекта C#, который нужно создать.

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:
* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/). Там же можно получать ответы на интересующие вас вопросы.
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio).  (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также
* [Обновление Visual Studio 2017](update-visual-studio.md)
* [Изменение Visual Studio 2017](modify-visual-studio.md)
* [Удаление Visual Studio 2017](uninstall-visual-studio.md)
* [Создание автономной установки Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Руководство администратора Visual Studio 2017](visual-studio-administrator-guide.md)
  * [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Установка средств сборки в контейнер](build-tools-container.md)
