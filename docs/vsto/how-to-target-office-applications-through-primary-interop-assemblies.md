---
title: "Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия"
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
  - "разработка приложений [разработка решений Office в Visual Studio], автоматизация"
  - "сборки [разработка решений Office в Visual Studio], ссылки основной сборки взаимодействия"
  - "Office - приложения [разработка решений Office в Visual Studio], автоматизация"
  - "Office - основные сборки взаимодействия в Visual Studio, добавление ссылок к"
  - "основные сборки взаимодействия [разработка решений Office в Visual Studio], добавление ссылок к"
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия
  При создании нового проекта Office Visual Studio автоматически добавляет ссылки на основные сборки взаимодействия \(PIA\) Microsoft Office, необходимые для построения проекта.  Ссылки на другие основные сборки взаимодействия необходимо добавлять в следующих случаях.  
  
-   Вы хотите использовать функции других приложений Microsoft Office в своем проекте.  Например, можно использовать функции Microsoft Office Excel в проекте для Microsoft Office Word.  
  
-   Вы хотите автоматизировать приложения Microsoft Office, у которых нет выделенных проектов в Visual Studio, например Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Добавление ссылки на основную сборку взаимодействия  
  
1.  Откройте проект Office и выберите имя проекта в **обозревателе решений**.  
  
2.  В меню **Проект** щелкните команду **Добавить ссылку**.  
  
3.  На вкладке **Платформа** выберите необходимую основную сборку взаимодействия в списке **Имя компонента**.  Дополнительные сведения о доступных основных сборках взаимодействия Microsoft Office см. в разделе [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
     Если проект предназначен для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, для свойства **Внедрить типы взаимодействия** для ссылки на сборку по умолчанию устанавливается значение **True**.  Благодаря применению этого параметра вашему решению на компьютерах конечных пользователей основная сборка взаимодействия не требуется.  Дополнительные сведения см. в разделе [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  В проектах Office всегда добавляйте ссылки на основные сборки взаимодействия Office на вкладке **.NET** в диалоговом окне**Добавить ссылку**, а не на вкладке **COM**.  Дополнительные сведения см. в разделе [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Нажмите кнопку **ОК**.  
  
     Имя сборки появляется в папке **Ссылкиобозревателя решений**.  
  
## См. также  
 [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Практическое руководство. Установка основных сборок взаимодействия Microsoft Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  