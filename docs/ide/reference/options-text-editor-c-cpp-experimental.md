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
translationtype: Human Translation
ms.sourcegitcommit: e9a05d008f671fb79d6813a14c594b82f27697e3
ms.openlocfilehash: 780c643c25f0d43ec0564e43bc50d2f36f1aee79
ms.lasthandoff: 03/27/2017

---
# <a name="options-text-editor-cc-experimental"></a>"Параметры", "Текстовый редактор", C/C++, "Экспериментальный"
Изменяя эти параметры, можно настроить поведение, связанное с IntelliSense и базой данных просмотра, при программировании на языке C или C++. Эти функции являются экспериментальными и могут быть удалены или изменены в будущем выпуске Visual Studio.  
  
 Чтобы открыть эту страницу, в диалоговом окне **Параметры** в левой области разверните **Текстовый редактор**, разверните **C/C++**и щелкните **Экспериментальный**.  

 Эти функции доступны в установке Visual Studio 2017.  
  
> [!NOTE]
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. См. раздел [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="enable-predictive-intellisense"></a>Включить прогнозный IntelliSense
Прогнозный IntelliSense ограничивает число результатов, отображаемых в раскрывающемся списке IntelliSense, чтобы вы видели лишь результаты, релевантные в данном контексте. Например, если ввести <code>int x =</code> и вызвать раскрывающийся список IntelliSense, вы увидите только целые числа или функции, которые их возвращают. По умолчанию прогнозный IntelliSense отключен.

## <a name="enable-faster-project-load"></a>Ускорение загрузки проекта
Этот параметр включает функцию "загрузка упрощенного решения". Когда она включена, Visual Studio не загружает проекты целиком, пока они не понадобятся вам. Многие распространенные задачи, такие как перемещение по базе кода, изменения кода и сборка проектов, не требуют загрузки проекта. Если этот параметр включен, вы можете быстрее приступить к выполнению этих стандартных задач, не ожидая загрузки проекта.  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Дополнительные функции в галерее Visual Studio
Список дополнительных функций текстового редактора в галерее Visual Studio можно найти [здесь](http://go.microsoft.com/fwlink/?LinkId=692016). Примером может служить расширение [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), которое поддерживает перечисленные ниже возможности.  
  
-   **Добавление недостающих операторов #include** — для неизвестных символов в коде предлагаются подходящие операторы #include.  
  
-   **Добавление пространства имен using и полное определение символа** — аналогично предыдущему пункту, но относится к пространствам имен.  
  
-   **Добавление недостающих точек с запятой**  
  
-   **Справка MSDN** — поиск информации о сообщении об ошибке на сайте MSDN.  
  
 Вы можете либо навести указатель на волнистую линию, чтобы появилась лампочка, либо нажать клавиши CTRL+точка (CTRL+.). Имейте в виду, что при использовании сочетания клавиш курсор не обязательно должен находиться в элементе с ошибкой или в токене. Для получения предложений по любым элементам в строке достаточно, чтобы курсор находился в этой строке.  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров языка редактора](../../ide/reference/setting-language-specific-editor-options.md)   
 [Рефакторинг в C++ (блог по VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)

