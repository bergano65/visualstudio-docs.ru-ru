---
title: "Шаг 11. Запуск программы и изучение других возможностей | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 12
author: kempb
ms.author: kempb
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 019d72fece70586013455bbe74f09b990c9fac80
ms.lasthandoff: 02/22/2017

---
# <a name="step-11-run-your-program-and-try-other-features"></a>Шаг 11. Запуск программы и изучение других возможностей
Разработка программа завершена и она готова для выполнения. Можно запустить программу и задать цвет фона для PictureBox. В качестве дополнительного занятия, попробуйте улучшить программу с помощью изменения цвета формы, настройки кнопок и флажков, изменения свойств формы.  
  
 Загрузить готовую версию примера можно на странице [Complete Picture Viewer tutorial sample](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8) (Полный пример учебного руководства по созданию приложения для просмотра рисунков).  
  
 ![ссылка на видео](../data-tools/media/playvideo.gif "воспроизвести_видео")Видеоверсию этой статьи см. на следующих страницах: [Tutorial 1: Create a Picture Viewer in Visual Basic - Video 5](http://go.microsoft.com/fwlink/?LinkId=205216) (Учебное руководство 1. Создание приложения для просмотра рисунков на Visual Basic — видео 5) или [Tutorial 1: Create a Picture Viewer in C# - Video 1](http://go.microsoft.com/fwlink/?LinkId=205206) (Учебное руководство 1. Создание приложения для просмотра рисунков на C# — видео 5). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.  
  
### <a name="to-run-your-program-and-set-the-background-color"></a>Запуск программы и настройка цвета фона  
  
1.  Нажмите клавишу F5 или в строке меню выберите **Отладка**, **Начать отладку**.  
  
2.  Прежде чем открыть изображение, нажмите кнопку **Установить цвет фона**. Откроется диалоговое окно **Цвет**.  
  
     ![Диалоговое окно "Цвет"](../ide/media/express_colordialog.png "Express_ColorDialog")  
Диалоговое окно "Цвет"  
  
3.  Выберите цвет фона для элемента управления PictureBox. Внимательно просмотрите метод `backgroundButton_Click()`, чтобы понять, как он работает.  
  
    > [!NOTE]
    >  Можно загрузить рисунок из Интернета путем вставки URL-адреса в диалоговое окно **Открытие файла**. Попробуйте найти изображение с прозрачным фоном, таким образом, чтобы был показан цвет фона.  
  
4.  Нажмите кнопку **Очистить рисунок**, чтобы обеспечить удаление рисунка. Затем выйдите из программы, нажав кнопку **Закрыть**.  
  
### <a name="to-try-other-features"></a>Изучение других возможностей  
  
-   Измените цвет формы и кнопок с помощью свойства **BackColor**.  
  
-   Настройте кнопки и флажки с помощью свойств **Font** и **ForeColor**.  
  
-   Измените свойства формы **FormBorderStyle** и **ControlBox**.  
  
-   Используйте свойства **AcceptButton** и **CancelButton**, чтобы кнопки автоматически нажимались, когда пользователь нажимает клавишу ВВОД или клавишу ESC. Сделайте так, чтобы программа открывала диалоговое окно **Открытие файла** при нажатии пользователем клавиши ВВОД и закрывала окно при нажатии клавиши ESC.  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Дополнительные сведения о программировании в Visual Studio см. в разделе [Основные понятия программирования](http://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6).  
  
-   Дополнительные сведения о Visual Basic см. в разделе [Разработка приложений с помощью Visual Basic](/dotnet/visual-basic/developing-apps/index).  
  
-   Дополнительные сведения о Visual C# см. в разделе [Введение в язык C# и .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).  
  
-   Следующее руководство см. на странице [Tutorial 2: Create a Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md) (Учебное руководство 2. Создание ограниченной по времени математической головоломки).  
  
-   Предыдущий шаг руководства см.в разделе [Step 10: Write Code for Additional Buttons and a Check Box](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md) (Шаг 10. Написание кода дополнительных кнопок и флажка).
