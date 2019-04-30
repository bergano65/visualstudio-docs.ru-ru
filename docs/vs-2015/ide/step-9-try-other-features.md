---
title: Шаг 9. Изучение других возможностей | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c8a701715c0adff479fa29dbe9c9b28287031dfd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428290"
---
# <a name="step-9-try-other-features"></a>Шаг 9. Изучение других возможностей
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для изучения других функций попробуйте изменить значки и цвета, добавить в игру таймер или звуки. Чтобы сделать игру интереснее, увеличьте игровое поле или измените настройки таймера.  
  
 Скачать готовую версию примера можно на странице [Complete Matching Game tutorial sample](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) (Полный пример руководства по созданию игры "Подбери пару!").  
  
### <a name="to-try-other-features"></a>Изучение других возможностей  
  
- Замените значки и цвета на другие.  
  
    > [!TIP]
    > Попробуйте проверить свойство [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) метки.  
  
- Добавьте таймер игры, который отслеживает время, необходимое игроку для победы.  
  
    > [!TIP]
    > Для этого можно добавить метку для отображения истекшего времени в форму над TableLayoutPanel и добавить в форму еще один таймер для отслеживания времени. Следующий код служит для запуска таймера, когда игрок начинает игру, и остановки таймера после сопоставления последних двух значков.  
  
- Добавьте звуки, которые будут воспроизводиться при нахождении игроком пары, отображении двух несовпадающих значков и повторном сокрытии значков программой.  
  
    > [!TIP]
    > Для воспроизведения звуков можно использовать пространство имен System.media. Дополнительные сведения см. в разделе [Воспроизведение звуков в приложении Windows Forms (C# .NET)](http://youtu.be/qOh4ooHg1UU) или [Воспроизведение звука в Visual Basic](http://youtu.be/-4oPDeQrtMs).  
  
- Сделайте игру труднее, увеличив игровое поле.  
  
    > [!TIP]
    > Необходимо не только добавить строки и столбцы в TableLayoutPanel, но и учесть количество создаваемых значков.  
  
- Сделайте игру интереснее, скрывая первый значок, если игрок действует медленно и не щелкает второй значок в течение определенного времени.  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
- Если у вас возникли затруднения или вопросы по программированию, попробуйте задать вопрос на одном из форумов MSDN. См. [Форум Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) и [Форум Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
- Также вы можете найти отличные бесплатные учебные видеоматериалы. Дополнительные сведения о программировании на языке Visual Basic, см. в разделе [основы Visual Basic: Разработка для начинающих](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Дополнительные сведения о программировании на языке Visual C#, см. в разделе [ C# основы: Разработка для начинающих](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
- Предыдущий раздел руководства: [Шаг 8. Добавление метода для проверки, выиграл ли игрок](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
