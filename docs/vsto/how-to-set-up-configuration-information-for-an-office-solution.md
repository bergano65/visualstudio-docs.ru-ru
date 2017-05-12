---
title: "Практическое руководство. Установка сведений о конфигурации для решений Office"
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
  - "файлы конфигурации [разработка решений Office в Visual Studio]"
  - "решения [разработка решений Office в Visual Studio], файлы конфигурации"
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Практическое руководство. Установка сведений о конфигурации для решений Office
  Для настройки параметров, относящихся к конкретным решениям Office, можно использовать файлы конфигурации.  Можно установить такие параметры как политика привязки сборки, удаленное взаимодействие объектов, параметры отладки и трассировки.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Добавление файла конфигурации к проекту Office  
  
1.  В меню **Проект** выберите команду **Добавить новый элемент**.  
  
2.  В панели **Категории** щелкните пункт **Общие**.  
  
3.  В панели **Шаблоны**, выберите пункт **Файл конфигурации приложения**.  
  
4.  В окне **Имя**, введите имя сборки с расширением CONFIG.  Например, файл конфигурации для сборки проекта Excel с именем ExcelWorkbook1.dll следует назвать ExcelWorkbook1.dll.config.  
  
5.  Нажмите кнопку **Добавить**.  
  
6.  Создайте файл конфигурации в соответствии со схемой файла конфигурации приложения.  Дополнительные сведения см. в разделе [Схема файлов конфигурации для .NET Framework](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38).  
  
 Никаких особых доводов в пользу использования файлов конфигурации с проектами Office не существует.  
  
## См. также  
 [Схема файлов конфигурации для .NET Framework](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  