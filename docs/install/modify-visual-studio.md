---
title: Изменение Visual Studio 2017 | Документация Майкрософт
description: Сведения о поэтапном изменении среды Visual Studio.
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3145b1fef86b6d9540e105557bdf40d291049a52
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="modify-visual-studio-2017-by-adding-or-removing-workloads-and-components"></a>Изменение Visual Studio 2017 путем добавления или удаления рабочих нагрузок и компонентов
Мы упростили не только персонализацию Visual Studio в соответствии с выполняемыми задачами, но и настройку самой среды Visual Studio. Для этого запустите установщик Visual Studio и внесите нужные изменения.

Ниже описывается порядок действий.  

## <a name="modify-workloads"></a>Изменение рабочих нагрузок  
 Рабочие нагрузки содержат функции, которые требуются для используемого языка программирования или платформы. С помощью рабочих нагрузок можно изменить среду Visual Studio так, чтобы она поддерживала выполнение нужных задач в любое время.  

>[!IMPORTANT]
>Чтобы установить, обновить или изменить среду Visual Studio, необходимо войти в учетную запись с правами администратора. Дополнительные сведения см. в разделе [Разрешения пользователей и Visual Studio](../ide/user-permissions-and-visual-studio.md).

1.  Найдите установщик Visual Studio на своем компьютере.  

     Например, на компьютере с Windows 10 нажмите кнопку **Пуск** и прокрутите список до буквы **V**, где расположен пункт **Visual Studio Installer**.  

     ![Установщик Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Поиск установщика Microsoft Visual Studio")

     >[!NOTE]
     На некоторых компьютерах установщик Visual Studio может быть указан под буквой **"M"** — для **Microsoft Visual Studio**.<br/><br/> Кроме того, Visual Studio Installer можно найти в следующем расположении: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2.  Щелкните установщик (или коснитесь его), чтобы запустить, и выберите команду **Изменить**.  

     ![Запустите или измените Visual Studio](media/modify-visual-studio.png "Изменение Visual Studio 2017")

     При наличии ожидающих обновлений кнопка "Изменить" будет находиться в другом месте. Нажмите кнопку **Дополнительно**, затем кнопку **Изменить**.   

     ![Обновление или изменение Visual Studio](media/modify-or-update-visual-studio.png "Обновление или изменение Visual Studio 2017")

3.  На экране **Рабочие нагрузки** выберите рабочие нагрузки, которые нужно установить, или отмените выбор тех, которые нужно удалить.  

    ![Диалоговое окно программы установки Visual Studio 2017](media/vs2017-modify-workloads.PNG "Выбор рабочей нагрузки в Visual Studio 2017")

4. Снова выберите команду **Изменить**.  

5. После установки новых рабочих нагрузок и компонентов выберите команду **Запуск**.

## <a name="modify-individual-components"></a>Изменение отдельных компонентов

Если вы не хотите пользоваться удобной функцией рабочих нагрузок для настройки установленного экземпляра Visual Studio, выберите в установщике Visual Studio вариант **Отдельные компоненты**, затем включите нужные компоненты и следуйте указаниям.  

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio воспользуйтесь инструкцией по [устранению неполадок и исправлению ошибок в ходе установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Вы можете также связаться с нами для помощи по установке в [интерактивном чате](https://www.visualstudio.com/vs/support/#talktous) (только английский язык). Дополнительные сведения см. на [странице Visual Studio "Свяжитесь с нами"](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:
* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем и искать решения в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/).
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio).  (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также
* [Установка Visual Studio 2017](install-visual-studio.md)
* [Обновление Visual Studio 2017](update-visual-studio.md)
* [Удаление Visual Studio 2017](uninstall-visual-studio.md)
