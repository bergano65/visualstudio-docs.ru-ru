---
title: 'Как: настроить сведения о конфигурации для решения Office | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9659872fa6cb4e294d1757412862c10e42cde2e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Практическое руководство. Установка сведений о конфигурации для решений Office
  Файлы конфигурации можно использовать для настройки параметров, относящихся к решениям Office. Можно указать параметры, такие как политика привязки сборок, удаленные объекты, отладки и параметры трассировки.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Чтобы добавить в проект файл конфигурации  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
2.  В **категории** области, нажмите кнопку **Общие**.  
  
3.  В **шаблоны** выберите **файла конфигурации приложения**.  
  
4.  В **имя** введите то же имя сборки с расширением config. Например файл конфигурации для сборки проекта Excel с именем ExcelWorkbook1.dll будет называться ExcelWorkbook1.dll.config.  
  
5.  Нажмите кнопку **Добавить**.  
  
6.  Создайте файл конфигурации в соответствии со схемой файла конфигурации приложения. Дополнительные сведения см. в разделе [схема файла конфигурации для платформы .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
 Нет никаких особенных условий для использования файлов конфигурации с проектами Office.  
  
## <a name="see-also"></a>См. также  
 [Схема файла конфигурации для платформы .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  