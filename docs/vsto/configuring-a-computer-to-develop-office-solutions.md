---
title: "Настройка компьютера для разработки решений Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 9b63b3b495b9cb15ea3e9eeedcecedb3a384f8a0
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Настройка компьютера для разработки решений Office

Чтобы создать надстройки VSTO и настройки для Microsoft Office, установите поддерживаемую версию Visual Studio, платформы .NET Framework и Microsoft Office.

|Программное обеспечение|Поддерживаемые версии|
|--------------|------------------------|
|Visual Studio 2017| Любой выпуск с **разработка приложений Office и SharePoint** рабочей нагрузки.|
|.NET Framework|-.NET Framework 4 или более поздней версии.|
|Microsoft Office|<ul><li>Любой выпуск набора Office, включая Office профессиональный плюс для Office 365.</li><li>Любое из следующих автономных приложений.<br /><br /> <ul><li>Excel</li><li>InfoPath (только в Office 2013 и Office 2010)</li><li>Outlook - приложение</li><li>PowerPoint</li><li>Проект</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic для приложений (VBA) должен быть установлен как часть Office. **Важно:** версии нажмите кнопку для запуска приложения Office 2010 не поддерживаются.|

Подробное описание шагов установки, в разделе [как: Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Если шаблоны проекта не отображаются или не работают в Visual Studio

Если установить поддерживаемую версию Visual Studio, платформы .NET Framework и Microsoft Office, но шаблонов проектов Office не отображаются в Visual Studio **новый проект** диалоговое окно, или ошибка при попытке использовать один, Проверьте следующее:

- Проверьте, установлены ли на компьютер инструменты разработчика Microsoft Office.

     Инструменты разработчика Office являются дополнительным компонентом Visual Studio, но обычно устанавливаются вместе с Visual Studio автоматически. Если во время установки Visual Studio вы указываете, какие функции нужно установить, обязательно выберите элемент **Инструменты разработчика Microsoft Office** .

     Чтобы убедиться в том, что средства установлены, запустите программу установки Visual Studio и выберите **изменить** кнопки. Установите флажок возле элемента **Инструменты разработчика Microsoft Office** и нажмите кнопку **Обновить** .

- Убедитесь в том, что вы не используете версию Office нажми щелкните к запуску. См. раздел [Практическое руководство. Как проверить, является ли установленная на компьютере программа Outlook приложением типа "нажми и работай"](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).

- Убедитесь, что у вас только одна версия Microsoft Office.

Если проблема остается, см. раздел [Additional Support for Errors in Office Solutions](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>См. также

[Приступая к работе &#40; разработка решений Office в Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Практическое руководство. Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Практическое руководство. Установка распространяемого пакета среды выполнения для инструментов Visual Studio для Office](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Практическое руководство. Установка основных сборок взаимодействия Microsoft Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Доступность функций по типам приложений Office и типам проектов](../vsto/features-available-by-office-application-and-project-type.md)
