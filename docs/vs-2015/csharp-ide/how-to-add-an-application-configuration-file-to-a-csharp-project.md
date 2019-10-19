---
title: Как добавить файл конфигурации приложения в C# проект | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667536"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Практическое руководство. Добавление файла конфигурации приложения в проект C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Добавив файл конфигурации приложения (файл app.config) в проект C#, вы можете настроить способ, которым общеязыковая среда выполнения будет находить и загружать файлы сборки. Дополнительные сведения о файлах конфигурации приложений см. [в разделе Обнаружение сборок в среде выполнения](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

> [!NOTE]
> Магазин Windows не поддерживает <xref:System.Configuration>. В результате приложения магазина не содержат шаблон App. config.

 При сборке проекта среда разработки автоматически копирует файл App. config, изменяет имя файла копии в соответствии с исполняемым файлом, а затем перемещает копию в каталог bin.

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Добавление файла конфигурации приложения в C# проект

1. В строке меню выберите **проект**, **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

2. Разверните узел **установленные**, **разверните C# элемент визуальные элементы**, а затем выберите шаблон **файл конфигурации приложения** .

3. В текстовом поле **Имя** введите имя и нажмите кнопку **Добавить**.

     Файл с именем App. config добавляется в проект.

## <a name="see-also"></a>См. также раздел
 [Управление параметрами приложения (.NET)](../ide/managing-application-settings-dotnet.md) [файл конфигурации схема](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38) [Настройка приложений](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f) [руководство. Настройка приложения для .NET Frameworkной версии](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717) [с помощью среды разработки Visual Studio для C# ](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)