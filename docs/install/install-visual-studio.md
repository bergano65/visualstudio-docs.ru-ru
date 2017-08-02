---
title: "Установка Visual Studio 2017 | Документация Майкрософт"
description: "Сведения о поэтапной установке среды Visual Studio."
ms.custom: 
ms.date: 05/16/2017
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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 9f7c1d33191adf3fb54cf59cd98ae5fffe14eee4
ms.contentlocale: ru-ru
ms.lasthandoff: 05/31/2017

---
# <a name="install-visual-studio-2017"></a>Установка Visual Studio 2017
Предлагаем ознакомиться с новым способом установки Visual Studio. В последней версии мы упростили выбор и установку нужных компонентов, что позволяет уменьшить объем требуемых для Visual Studio ресурсов системы и ускорить установку.

Вы хотите ознакомиться с другими новыми возможностями? Обратитесь к [заметкам о выпуске](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes). Более подробные сведения о том, как мы переработали процедуру установки, см. в записях блога [Более быстрый и эффективный установщик Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/) и [Разбор оптимизированной процедуры установки Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/).  

Готовы к установке? Мы последовательно опишем каждое действие.

## <a name="check-system-requirements"></a>Проверка требований к системе
Перед началом установки проверьте [требования к системе](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs), чтобы убедиться, что компьютер готов к установке Visual Studio 2017.

## <a name="download-visual-studio"></a>Скачивание Visual Studio
Прежде всего, необходимо скачать Visual Studio. Чтобы сделать это, нажмите кнопку ниже, нажмите **Сохранить**, а затем — **Открыть папку**.

 > [!div class="button"]
 > [Скачивание Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="install-the-installer"></a>Установка установщика  
После скачивания Visual Studio 2017 вы получаете файл начальной загрузки, который, в свою очередь, устанавливает новый облегченный установщик. В этом новом установщике есть все необходимое для настройки установки.  

> [!IMPORTANT]
> Если на вашем компьютере установлена предварительная версия Visual Studio 2017, вам будет предложено удалить ее перед установкой Visual Studio 2017.

1.  В папке **Загрузки** дважды щелкните файл загрузчика, который соответствует или аналогичен одному из следующих файлов:

  * **vs_enterprise.exe** для Visual Studio Enterprise;
  * **vs_professional.exe** для Visual Studio Professional;
  * **vs_community.exe** для Visual Studio Community.  <br><br>

  Если появляется оповещение системы контроля учетных записей, нажмите кнопку **Да**.  

2.  Мы попросим вас принять [условия лицензии](https://www.visualstudio.com/license-terms/) и [заявление о конфиденциальности](https://go.microsoft.com/fwlink/?LinkID=824704) корпорации Майкрософт. Нажмите кнопку **Продолжить**.  

   ![Условия лицензии и заявление о конфиденциальности](~/docs/install/media/vs2017-privacy-and-license-terms.PNG "Условия лицензии и заявление о конфиденциальности корпорации Майкрософт")  

Появятся несколько экранов состояния, на которых показан ход установки. Когда установка установщика завершится, можно приступить к выбору требуемых наборов функций или рабочих нагрузок.

## <a name="install-workloads"></a>Установка рабочих нагрузок  
 Вы можете настроить установку с помощью рабочих нагрузок. Выберите одну или несколько рабочих нагрузок. Каждая из них содержит требуемые функции для языка программирования или платформы.  

 Ниже описывается, как их получить.  

1.  Найдите нужную рабочую нагрузку на экране **Установка Visual Studio**.  

  ![Диалоговое окно установки Visual Studio 2017](~/docs/install/media/vs2017-workloads.PNG "Установка рабочих нагрузок Visual Studio")

     Например, выберите рабочую нагрузку "Разработка классических приложений .NET". В нее входит основной редактор кода по умолчанию, который предоставляет базовую поддержку редактирования кода для более чем 20 языков, возможность открывать и изменять код в любой папке без наличия проекта и интегрированное управление исходным кодом.  

2.  Выбрав нужные рабочие нагрузки, нажмите кнопку **Установить**.  

    Далее появятся экраны состояния, на которых показан ход установки Visual Studio.

3.  После установки новых рабочих нагрузок и компонентов нажмите кнопку **Запуск**.

## <a name="install-individual-components"></a>Установка отдельных компонентов

Если вы не хотите пользоваться удобной функцией рабочих нагрузок для настройки установленного экземпляра Visual Studio, щелкните в установщике Visual Studio вариант **Отдельные компоненты**, затем выберите нужные компоненты и следуйте указаниям.

  ![Visual Studio 2017 — установка отдельных компонентов](~/docs/install/media/vs2017-components.PNG "Установка отдельных компонентов Visual Studio")

## <a name="install-language-packs"></a>Установка языковых пакетов

Чтобы установить Visual Studio 2017 на нужном языке, выберите в установщике Visual Studio пункт **Языковые пакеты** и следуйте указаниям.

  ![Visual Studio 2017 — установка языковых пакетов](~/docs/install/media/vs2017-languages.PNG "Установка языковых пакетов Visual Studio")

### <a name="change-the-installer-language"></a>Изменение языка установщика

По умолчанию при первом запуске установщик пытается использовать язык операционной системы. Эта настройка сохраняется. Вы можете изменить ее, запустив установщик из командной строки. Например, можно принудительно запустить установщик на английском языке, выполнив команду `vs_installer.exe --locale en-US`. Программа установки запомнит этот параметр и использует его при следующем запуске. Установщик поддерживает следующие токены языков: zh-CN, zh-TW, cs-CZ, en-US, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU, es-ES и tr-TR.

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio ознакомьтесь с советами, приведенными на странице [Устранение неполадок и исправление ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md).

## <a name="see-also"></a>См. также  
* [Изменение Visual Studio 2017](modify-visual-studio.md)
* [Обновление Visual Studio 2017](update-visual-studio.md)
* [Удаление Visual Studio 2017](uninstall-visual-studio.md)
* [Руководство администратора Visual Studio 2017](visual-studio-administrator-guide.md)
* [Как сообщить о проблеме с Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

