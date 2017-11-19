---
title: "Как: настроить сведения о конфигурации для решения Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a8c2e0a904ad3cdbef3e70072d263cc26274de52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
  
  