---
title: "Изменение Visual Studio 2017 | Документация Майкрософт"
description: "Сведения о поэтапном изменении среды Visual Studio."
ms.custom: H1Hack27Feb2017
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: f003d5f5a598971d27c55e90ba3bbfbfdc5ae1f1
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2017
---
# <a name="modify-visual-studio-2017-by-adding-or-removing-workloads-and-components"></a>Изменение Visual Studio 2017 путем добавления или удаления рабочих нагрузок и компонентов
Мы упростили не только персонализацию Visual Studio в соответствии с выполняемыми задачами, но и настройку самой среды Visual Studio. Теперь больше не нужно обращаться к панели управления. Вместо этого запустите Visual Studio Installer и внесите нужные изменения.

Ниже описывается порядок действий.  

## <a name="modify-workloads"></a>Изменение рабочих нагрузок  
 Рабочие нагрузки содержат функции, которые требуются для используемого языка программирования или платформы. С помощью рабочих нагрузок можно изменить среду Visual Studio так, чтобы она поддерживала выполнение нужных задач в любое время.  

>[!IMPORTANT]
>Чтобы установить, обновить или изменить среду Visual Studio, необходимо войти в учетную запись с правами администратора. Дополнительные сведения см. в разделе [Разрешения пользователей и Visual Studio](../ide/user-permissions-and-visual-studio.md).

1.  Найдите установщик Visual Studio на своем компьютере.  

     Например, на компьютере с юбилейным обновлением Windows 10 нажмите кнопку **Пуск** и прокрутите список до буквы **V**, где расположен пункт **Visual Studio Installer**.  

     ![Установщик Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Поиск установщика Microsoft Visual Studio")

     >[!NOTE]
     На некоторых компьютерах установщик Visual Studio может быть указан под буквой **"M"** — для **Microsoft Visual Studio**.<br/><br/> Кроме того, Visual Studio Installer можно найти в следующем расположении: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2.  Щелкните установщик (или коснитесь его) и выберите действие **Изменить**.  

     ![Запустите или измените Visual Studio](media/vs2017-modify.PNG "Изменение Visual Studio 2017")  

3.  На экране **Рабочие нагрузки** выберите рабочие нагрузки, которые нужно установить, или отмените выбор тех, которые нужно удалить.  

    ![Диалоговое окно программы установки Visual Studio 2017](media/vs2017-modify-workloads.PNG "Выбор рабочей нагрузки в Visual Studio 2017")

4. Еще раз щелкните или коснитесь **Изменить**.  

5. После установки новых рабочих нагрузок и компонентов нажмите кнопку **Запуск**.

## <a name="modify-individual-components"></a>Изменение отдельных компонентов

Если вы не хотите пользоваться удобной функцией рабочих нагрузок для настройки установленного экземпляра Visual Studio, выберите в установщике Visual Studio вариант **Отдельные компоненты**, выберите нужные компоненты и следуйте указаниям.  

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:
* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/). Там же можно получать ответы на интересующие вас вопросы.
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio).  (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также
* [Установка Visual Studio 2017](install-visual-studio.md)
* [Обновление Visual Studio 2017](update-visual-studio.md)
* [Удаление Visual Studio 2017](uninstall-visual-studio.md)
