---
title: "&quot;Параметры&quot;, &quot;Текстовый редактор&quot;, C/C++, &quot;Экспериментальный&quot; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 77c4408fcd93a776468cf5fb23b3807a2b8d594d
ms.contentlocale: ru-ru
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-cc-experimental"></a>"Параметры", "Текстовый редактор", C/C++, "Экспериментальный"
Изменяя эти параметры, можно настроить поведение, связанное с IntelliSense и базой данных просмотра, при программировании на языке C или C++. Эти функции являются экспериментальными и могут быть удалены или изменены в будущем выпуске Visual Studio. В этом разделе описываются параметры в Visual Studio 2017. По Visual Studio 2015 см. раздел [Параметры, текстовый редактор, C/C++, экспериментальный](https://msdn.microsoft.com/library/mt591979.aspx) 
  
 Чтобы получить доступ к этой странице свойств, нажмите клавиши **CONTROL+Q** для активации `Quick Launch`, а затем введите "experimental". Функция быстрого запуска найдет страницу после ввода первых нескольких букв. Также для перехода на нее можно выбрать **Сервис | Параметры**, развернуть **Текстовый редактор**, а затем **C/C++** и выбрать **Экспериментальный**.  

 Эти функции доступны в установке Visual Studio 2017.  
  
> [!NOTE]
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. См. статью [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="enable-predictive-intellisense"></a>Включить прогнозный IntelliSense
Прогнозный IntelliSense ограничивает число результатов, отображаемых в раскрывающемся списке IntelliSense, чтобы вы видели лишь результаты, релевантные в данном контексте. Например, если ввести <code>int x =</code> и вызвать раскрывающийся список IntelliSense, вы увидите только целые числа или функции, которые их возвращают. По умолчанию прогнозный IntelliSense отключен.

## <a name="enable-faster-project-load"></a>Ускорение загрузки проекта
Этот параметр позволяет Visual Studio кэшировать данные проекта, чтобы при открытии проекта он мог загрузить эти данные, а не повторно вычислять их из файлов проекта. Использование кэшированных файлов может значительно ускорить время загрузки проектов.  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Дополнительные функции в галерее Visual Studio
Список дополнительных функций текстового редактора в галерее Visual Studio можно найти [здесь](http://go.microsoft.com/fwlink/?LinkId=692016). Примером может служить расширение [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), которое поддерживает перечисленные ниже возможности.  
  
-   **Добавление недостающих операторов #include** — для неизвестных символов в коде предлагаются подходящие операторы #include.  
  
-   **Добавление пространства имен using и полное определение символа** — аналогично предыдущему пункту, но относится к пространствам имен.  
  
-   **Добавление недостающих точек с запятой.**  
  
-   **Справка MSDN** — поиск информации о сообщении об ошибке на сайте MSDN.  
  
 Вы можете либо навести указатель на волнистую линию, чтобы появилась лампочка, либо нажать клавиши CTRL+точка (CTRL+.). Имейте в виду, что при использовании сочетания клавиш курсор не обязательно должен находиться в элементе с ошибкой или в токене. Для получения предложений по любым элементам в строке достаточно, чтобы курсор находился в этой строке.  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров языка редактора](../../ide/reference/setting-language-specific-editor-options.md)   
 [Рефакторинг в C++ (блог по VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)

