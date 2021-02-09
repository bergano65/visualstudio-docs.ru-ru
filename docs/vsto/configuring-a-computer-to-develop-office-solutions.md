---
title: Настройка компьютера для разработки решений Office
description: Узнайте, как можно установить поддерживаемую версию Visual Studio, платформа .NET Framework и Microsoft Office, чтобы можно было создавать надстройки и настройки VSTO для Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee8f840aa81d3decfdb96dd2658b758704443347
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910572"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Настройка компьютера для разработки решений Office

Чтобы создать надстройки VSTO и настройки для Microsoft Office, установите поддерживаемую версию Visual Studio, платформы .NET Framework и Microsoft Office.

|Программное обеспечение|Поддерживаемые версии|
|--------------|------------------------|
|Visual Studio 2017| Любой выпуск с рабочей нагрузкой для **разработки Office или SharePoint** .|
|.NET Framework|— Платформа .NET Framework 4 или более поздней версии.|
|Microsoft Office|<ul><li>Любой выпуск пакета Office, включая Microsoft 365 приложения для предприятия.</li><li>Любое из следующих автономных приложений.<br /><br /> <ul><li>Excel</li><li>InfoPath (только в Office 2013 и Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic для приложений (VBA) должен быть установлен как часть Office. **Важно.** Не поддерживаются версии приложений Office 2010, выполняемые по щелчку мыши.|

Подробные инструкции по установке см. в разделе [руководство. Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Если шаблоны проектов не отображаются или не работают в Visual Studio

Если вы установили поддерживаемую версию Visual Studio, платформа .NET Framework и Microsoft Office, но шаблоны Office Project не отображаются в диалоговом окне **Новый проект** Visual Studio или при попытке его использования появляется сообщение об ошибке, проверьте следующее:

- Проверьте, установлены ли на компьютер инструменты разработчика Microsoft Office.

     Средства разработчика Office — это дополнительный компонент Visual Studio, но они устанавливаются автоматически вместе с Visual Studio. Если во время установки Visual Studio вы указываете, какие функции нужно установить, обязательно выберите элемент **Инструменты разработчика Microsoft Office** .

     Чтобы убедиться, что эти средства установлены, запустите программу установки Visual Studio и нажмите кнопку **Modify (изменить** ). Установите флажок возле элемента **Инструменты разработчика Microsoft Office** и нажмите кнопку **Обновить** .

- Убедитесь, что вы не используете версию Office, которая была доставлена с помощью команды "запустить". См. раздел [как проверить, является ли Outlook приложением, выполняющимся по щелчку на компьютере](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Убедитесь, что используется только одна версия Microsoft Office.

Если вы продолжаете испытывать проблемы, см. раздел [Дополнительная поддержка ошибок в решениях Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>См. также раздел
- [Приступая к работе &#40;разработке решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Как настроить компьютер для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Руководство. Установка распространяемого пакета среды выполнения Office Инструменты Visual Studio](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Руководство. Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Возможности, доступные по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md)