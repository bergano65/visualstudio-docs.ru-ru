---
title: "Практическое руководство. Задание значка приложения (Visual Basic, C#) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 18
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6889879efe06e8b0541aa08017292a92a736ea50
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Практическое руководство. Задание значка приложения (Visual Basic, C#)
Свойство `Icon` проекта указывает файл значка (ICO), который будет отображаться в скомпилированном приложении в проводнике и на панели задач Windows.  
  
 Доступ к свойству `Icon` можно получить в панели **Приложение** **конструктора проектов**. Оно содержит список значков, которые были добавлены в проект как ресурсы или файлы содержимого.  
  
> [!NOTE]
>  После задания свойства значка для приложения можно также задать свойство `Icon` каждого **окна** или **формы** в приложении. Сведения о значках окон для автономных приложений Windows Presentation Foundation (WPF) см. в разделе о свойстве <xref:System.Windows.Window.Icon%2A>.  
  
### <a name="to-specify-an-application-icon"></a>Указание значка приложения  
  
1.  В **обозревателе решений** выберите узел проекта (не узел **Решение**).  
  
2.  В строке меню выберите **Проект**, **Свойства**.  
  
3.  Когда откроется **Конструктор проектов**, выберите вкладку **Приложение**.  
  
4.  **(Visual Basic)** В списке **Значок** выберите файл значка (ICO).  
  
     **C#** Рядом со списком **Значок** нажмите кнопку **\<Обзор... >**, а затем перейдите в расположение файла значка.  
  
## <a name="see-also"></a>См. также  
 [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Управление свойствами приложения](../ide/application-properties.md)  
 [Практическое руководство. Добавление или удаление ресурсов](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)
