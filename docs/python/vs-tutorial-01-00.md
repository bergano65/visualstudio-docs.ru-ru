---
title: "Работа с Python в Visual Studio, шаг 0. Установка | Документы Майкрософт"
ms.custom: 
ms.date: 11/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: e0a9719ba9b686586ef13f13fbcaeb0c6de6c9ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="install-python-support-in-visual-studio"></a>Установка поддержки Python в Visual Studio

> [!Note]
> Сейчас Python поддерживается только в Visual Studio для Windows. В Mac и Linux его поддержка реализуется посредством Visual Studio Code. См. [Вопросы и ответы](python-in-visual-studio.md#questions-and-answers).

1. Скачайте и запустите последнюю версию установщика Visual Studio 2017 для Windows (поддержка Python имеется в выпуске 15.2 и более поздних).

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted">Установить Visual Studio 2017 Community</a>

    >[!Tip]
    > Выпуск Community предназначен для индивидуальных разработчиков, использования при аудиторном обучении и в научных исследованиях, а также разработки решений с открытым кодом. В других целях установите <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted">Visual Studio 2017 Professional</a> или <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted">Visual Studio 2017 Enterprise</a>.
    
1. В установщике предлагается список рабочих нагрузок, то есть групп связанных параметров для определенных целей разработки. Для Python выберите рабочую нагрузку **Разработка на Python** и нажмите **Установить**.

    ![Рабочая нагрузка разработки Python в установщике Visual Studio](media/installation-python-workload.png)

1. Чтобы быстро протестировать поддержку Python, запустите Visual Studio, нажмите клавиши ALT+I, чтобы открыть интерактивное окно Python, и введите `2+2`. Если вы не увидите результат `4`, проверьте выполненные действия.

    ![Тестирование Python в интерактивном окне](media/installation-interactive-test.png)

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Шаг 1. Создание проекта Python](vs-tutorial-01-01.md)

## <a name="see-also"></a>См. также

- [Создание среды для существующего интерпретатора Python](python-environments.md#creating-an-environment-for-an-existing-interpreter).
- [Установка поддержки Python в Visual Studio 2015 и более ранних версиях](installation.md).
- [Расположения установки](installation.md#install-locations).

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
