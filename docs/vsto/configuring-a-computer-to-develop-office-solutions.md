---
title: "Настройка компьютера для разработки решений Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Разработка приложений Office в Visual Studio, установка инструментов"
ms.assetid: 0b481186-fd31-43bf-aa4a-591f94309555
caps.latest.revision: 97
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Настройка компьютера для разработки решений Office
  Чтобы создать надстройки VSTO и настройки для Microsoft Office, установите поддерживаемую версию Visual Studio, платформы .NET Framework и Microsoft Office.  
  
|Программное обеспечение|Поддерживаемые версии|  
|-----------------------------|---------------------------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)] **Important:**  Во время установки необходимо установить флажок "Инструменты разработчика Microsoft Office".|  
|.NET Framework|-   .NET Framework 4 или более поздние версии.|  
|Microsoft Office|<ul><li>Любой выпуск набора Office, включая Office профессиональный плюс для Office 365.</li><li>Любое из следующих автономных приложений.<br /><br /> <ul><li>Excel</li><li>InfoPath \(только в Office 2013 и Office 2010\)</li><li>Outlook \- приложение</li><li>PowerPoint</li><li>Проект</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic для приложений \(VBA\) должен быть установлен как часть Office. **Important:**  Версии приложения Office 2010 типа "нажми и работай" не поддерживаются.|  
  
 Подробное описание шагов установки см. в разделе [Практическое руководство. Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
## Если шаблоны проекта не отображаются или не работают в Visual Studio  
 Если вы установили поддерживаемую версию Visual Studio, платформу .NET Framework и Microsoft Office, а шаблоны проекта Office или не отображаются в диалоговом окне Visual Studio **Новый проект**, или при попытке использовать один из них происходит ошибка, выполните указанные ниже действия.  
  
-   Проверьте, установлены ли на компьютер инструменты разработчика Microsoft Office.  
  
     Инструменты разработчика Office являются дополнительным компонентом Visual Studio, но обычно устанавливаются вместе с Visual Studio автоматически. Если во время установки Visual Studio вы указываете, какие функции нужно установить, обязательно выберите элемент **Инструменты разработчика Microsoft Office**.  
  
     Чтобы проверить, установлены ли эти инструменты, запустите программу установки Visual Studio и нажмите кнопку **Изменить**. Установите флажок возле элемента **Инструменты разработчика Microsoft Office** и нажмите кнопку **Обновить**.  
  
-   Убедитесь, что вы не используете версию Office типа "нажми и работай". См. раздел [Практическое руководство. Как проверить, является ли установленная на компьютере программа Outlook приложением типа "нажми и работай"](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).  
  
-   Должна выполняться только одна версия Microsoft Office.  
  
 Если проблема остается, см. раздел [Дополнительные сведения об ошибках в решениях Office](../vsto/additional-support-for-errors-in-office-solutions.md).  
  
## См. также  
 [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Практическое руководство. Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Практическое руководство. Установка распространяемого пакета среды выполнения Visual Studio Tools for Office](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Практическое руководство. Установка основных сборок взаимодействия Microsoft Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md)  
  
  