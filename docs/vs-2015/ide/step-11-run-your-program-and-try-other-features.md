---
title: Шаг 11. Запуск программы и изучение других возможностей | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac7d0896d501803a04da5bf9626e2b9e4716d41a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442653"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Шаг 11. Запуск программы и изучение других функций
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Разработка программа завершена и она готова для выполнения. Можно запустить программу и задать цвет фона для PictureBox. В качестве дополнительного занятия, попробуйте улучшить программу с помощью изменения цвета формы, настройки кнопок и флажков, изменения свойств формы.  
  
 Загрузить готовую версию примера можно на странице [Complete Picture Viewer tutorial sample](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8) (Полный пример учебного руководства по созданию приложения для просмотра рисунков).  
  
 ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo")видеоверсию этого раздела, см. в разделе [учебник 1: Create a Picture Viewer in Visual Basic — видео 5](http://go.microsoft.com/fwlink/?LinkId=205216) или [учебник 1: Create a Picture Viewer в C# — видео 5](http://go.microsoft.com/fwlink/?LinkId=205206). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.  
  
### <a name="to-run-your-program-and-set-the-background-color"></a>Запуск программы и настройка цвета фона  
  
1. Нажмите клавишу F5 или в строке меню выберите **Отладка**, **Начать отладку**.  
  
2. Прежде чем открыть изображение, нажмите кнопку **Установить цвет фона**. Откроется диалоговое окно **Цвет**.  
  
     ![Диалоговое окно "Цвет"](../ide/media/express-colordialog.png "Express_ColorDialog")  
Диалоговое окно "Цвет"  
  
3. Выберите цвет фона для элемента управления PictureBox. Внимательно просмотрите метод `backgroundButton_Click()`, чтобы понять, как он работает.  
  
    > [!NOTE]
    > Можно загрузить рисунок из Интернета путем вставки URL-адреса в диалоговое окно **Открытие файла**. Попробуйте найти изображение с прозрачным фоном, таким образом, чтобы был показан цвет фона.  
  
4. Нажмите кнопку **Очистить рисунок**, чтобы обеспечить удаление рисунка. Затем выйдите из программы, нажав кнопку **Закрыть**.  
  
### <a name="to-try-other-features"></a>Изучение других возможностей  
  
- Измените цвет формы и кнопок с помощью свойства **BackColor**.  
  
- Настройте кнопки и флажки с помощью свойств **Font** и **ForeColor**.  
  
- Измените свойства формы **FormBorderStyle** и **ControlBox**.  
  
- Используйте свойства **AcceptButton** и **CancelButton**, чтобы кнопки автоматически нажимались, когда пользователь нажимает клавишу ВВОД или клавишу ESC. Сделайте так, чтобы программа открывала диалоговое окно **Открытие файла** при нажатии пользователем клавиши ВВОД и закрывала окно при нажатии клавиши ESC.  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
- Дополнительные сведения о программировании в Visual Studio см. в разделе [Основные понятия программирования](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6).  
  
- Дополнительные сведения о Visual Basic см. в разделе [Разработка приложений с помощью Visual Basic](http://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f).  
  
- Дополнительные сведения о Visual C# см. в разделе [Введение в язык C# и .NET Framework](http://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081).  
  
- Следующее руководство см. в разделе [ Руководство 2. Создание математической викторины](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
- Предыдущий раздел руководства: [Шаг 10. Написание кода дополнительных кнопок и типа "флажок"](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
