---
title: Как выполнить Установка сведений о конфигурации для решения Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9db171b038178c9fe0bd4ffc4fbb98b221b9b4d5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864479"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Как выполнить Установка сведений о конфигурации для решения Office
  Файлы конфигурации можно использовать для настройки параметров, относящихся к решениям Office. Можно указать параметры, такие как политику привязки сборок, удаленные объекты, отладки и параметры трассировки.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Чтобы добавить файл конфигурации в проект Office  
  
1. В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
2. В **категории** панели щелкните **Общие**.  
  
3. В **шаблоны** области выберите **файла конфигурации приложения**.  
  
4. В **имя** и введите имя, совпадающее как сборки, а также добавляется расширение *.config*. Например, файл конфигурации для сборки проекта Excel с именем *ExcelWorkbook1.dll* будет называться *ExcelWorkbook1.dll.config*.  
  
5. Нажмите кнопку **Добавить**.  
  
6. Создание файла конфигурации в соответствии со схемой файл конфигурации приложения. Дополнительные сведения см. в разделе [схема файла конфигурации для .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
   Существует никаких особенных условий для использования файлов конфигурации с проектами Office.  
  
## <a name="see-also"></a>См. также  
 [Схема файла конфигурации для .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
