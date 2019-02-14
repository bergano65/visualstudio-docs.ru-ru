---
title: Как выполнить Задание значка приложения (Visual Basic, C#) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f794f1c988215f8899dce495f725b3a9c14a435
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788169"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Практическое руководство. Задание значка приложения (Visual Basic, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>См. также раздел  
 [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Управление свойствами приложения](../ide/application-properties.md)  
 [Практическое руководство. Добавление или удаление ресурсов](http://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
