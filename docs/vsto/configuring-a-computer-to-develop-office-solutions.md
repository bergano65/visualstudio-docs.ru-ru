---
title: "Настройка компьютера для разработки решений Office | Документы Microsoft"
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
helpviewer_keywords: Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c3e0ab446cb2aa65d0ec90aea596308ec4dcafec
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Настройка компьютера для разработки решений Office
  Чтобы создать надстройки VSTO и настройки для Microsoft Office, установите поддерживаемую версию Visual Studio, платформы .NET Framework и Microsoft Office.  
  
|Программное обеспечение|Поддерживаемые версии|  
|--------------|------------------------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)]**Важно:** во время установки необходимо выбрать флажок инструменты разработчика Microsoft Office.|  
|.NET Framework|-.NET Framework 4 или более поздней версии.|  
|Microsoft Office|<ul><li>Любой выпуск набора Office, включая Office профессиональный плюс для Office 365.</li><li>Любое из следующих автономных приложений.<br /><br /> <ul><li>Excel</li><li>InfoPath (только в Office 2013 и Office 2010)</li><li>Outlook - приложение</li><li>PowerPoint</li><li>Проект</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic для приложений (VBA) должен быть установлен как часть Office. **Важно:** версии нажмите кнопку для запуска приложения Office 2010 не поддерживаются.|  
  
 Подробное описание шагов установки, в разделе [как: Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Если шаблоны проекта не отображаются или не работают в Visual Studio  
 Если установить поддерживаемую версию Visual Studio, платформы .NET Framework и Microsoft Office, но шаблонов проектов Office не отображаются в Visual Studio **новый проект** диалоговое окно, или ошибка при попытке использовать один, Проверьте следующее:  
  
-   Проверьте, установлены ли на компьютер инструменты разработчика Microsoft Office.  
  
     Инструменты разработчика Office являются дополнительным компонентом Visual Studio, но обычно устанавливаются вместе с Visual Studio автоматически. Если во время установки Visual Studio вы указываете, какие функции нужно установить, обязательно выберите элемент **Инструменты разработчика Microsoft Office** .  
  
     Чтобы проверить, установлены ли эти инструменты, запустите программу установки Visual Studio и нажмите кнопку **Изменить** . Установите флажок возле элемента **Инструменты разработчика Microsoft Office** и нажмите кнопку **Обновить** .  
  
-   Убедитесь, что вы не используете версию Office типа "нажми и работай". См. раздел [Практическое руководство. Как проверить, является ли установленная на компьютере программа Outlook приложением типа "нажми и работай"](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).  
  
-   Убедитесь, что у вас только одна версия Microsoft Office.  
  
 Если проблема остается, см. раздел [Additional Support for Errors in Office Solutions](../vsto/additional-support-for-errors-in-office-solutions.md).  
  
## <a name="see-also"></a>См. также  
 [Приступая к работе &#40; разработка решений Office в Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Как: Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Как: Установка набора средств Visual Studio для распространяемого пакета среды выполнения Office](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Как: Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Доступность функций по типам приложений Office и типам проектов](../vsto/features-available-by-office-application-and-project-type.md)  
  
  