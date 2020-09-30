---
title: Настройка сведений о конфигурации для решения Office
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: e47ad00e3f9e90913784196894d514a755699864
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91581043"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Как настроить сведения о конфигурации для решения Office
  Файлы конфигурации можно использовать для настройки параметров, относящихся к решениям Office. Можно задать такие параметры, как политика привязки сборок, объекты удаленного взаимодействия, отладка и параметры трассировки.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Добавление файла конфигурации в проект Office

1. В меню **Проект** выберите **Добавить новый элемент**.

2. В области **категории** щелкните **Общие**.

3. В области **шаблоны** выберите **файл конфигурации приложения**.

4. В поле **имя** введите имя сборки и расширение *config*. Например, файл конфигурации для сборки проекта Excel с именем *ExcelWorkbook1.dll* будет называться *ExcelWorkbook1.dll.config*.

5. Нажмите кнопку **Добавить**.

6. Создайте файл конфигурации в соответствии со схемой файла конфигурации приложения. Дополнительные сведения см. [в разделе Схема файла конфигурации для .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   Нет особых рекомендаций по использованию файлов конфигурации с проектами Office.

## <a name="see-also"></a>См. также
- [Схема файла конфигурации для .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
