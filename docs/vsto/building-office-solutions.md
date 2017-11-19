---
title: "Построение решений Office | Документы Microsoft"
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
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
ms.assetid: c4b79ea8-df70-4a72-b76e-26e337d65727
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3df5fca6d41070b09ceb8b8be9b05212b7caa69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="building-office-solutions"></a>Построение решений Office
  Сборка и отладка проектов Office в принципе не отличается от сборки и отладки других типов проектов в Visual Studio, например Windows Forms. В этом разделе описываются существующие различия. Общие сведения о построении приложений см. в разделе [компилирование и сборка в Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
> [!NOTE]  
>  Заинтересованы в разработке решений, расширяющих возможности Office через [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и их можно создавать с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="project-output-for-office-projects"></a>Выходные файлы проекта Office  
 Выходным каталогом проектов Office является каталог *имя_проекта*\bin\release или *имя_проекта*\bin\debug. Нельзя выполнять сборку в каталог развертывания.  
  
### <a name="document-level-projects"></a>Проекты уровня документа  
 При сборке проекта уровня документа в выходной каталог проекта включаются следующие элементы:  
  
-   копия документа проекта;  
  
-   сборка проекта и все связанные сборки, свойству **Копировать локально** которых присвоено значение **true**;  
  
-   манифест приложения с расширением MANIFEST; дополнительные сведения см. в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md);  
  
-   манифест развертывания с расширением VSTO; дополнительные сведения см. в разделе [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md);  
  
-   файл базы данных программы (PDB).  
  
> [!NOTE]  
>  Если сборка решения выполняется не на локальный компьютер, а в удаленное расположение, добавьте полный путь к нему в список надежных расположений в центре управления безопасностью приложения. Дополнительные сведения см. в подразделе "Присвоение уровня доверия документам" раздела [Securing Office Solutions](../vsto/securing-office-solutions.md).  
  
### <a name="application-level-projects"></a>Проекты уровня приложения  
 При сборке проекта надстройки VSTO в выходной каталог проекта помещаются следующие элементы:  
  
-   сборка проекта и все связанные сборки, свойству **Копировать локально** которых присвоено значение **true**;  
  
-   манифест приложения с расширением MANIFEST; дополнительные сведения см. в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md);  
  
-   манифест развертывания с расширением VSTO; дополнительные сведения см. в разделе [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md);  
  
-   файл базы данных программы (PDB) для сборки проекта.  
  
 При сборке проектов надстроек VSTO на компьютере разработчика также создаются записи в реестре, необходимые для загрузки надстройки VSTO. Для получения дополнительной информации см. [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 При сборке проекта надстройки Outlook VSTO, содержащего области формы, в реестр добавляются следующие дополнительные данные:  
  
-   Раздел для каждого класса сообщений, связанного с одной или несколькими областями формы.  
  
-   Запись для каждой области формы и соответствующее значение, представляющее имя надстройки Outlook VSTO.  
  
 Приложение Outlook использует эту информацию для загрузки областей форм.  
  
## <a name="referenced-assemblies"></a>Связанные сборки  
 Вы можете ссылаться на сборки (включая проекты библиотеки классов) из проекта сборки решений Office. Каждая сборка, на которую существует ссылка, имеет свойство **Копировать локально**. Свойство**Копировать локально** указывает, копируется ли сборка в выходной каталог. По умолчанию для этого свойства установлено значение **true**. Каждая связанная сборка, свойству **Копировать локально** которой присвоено значение **true** , копируется в выходной каталог.  
  
## <a name="security-during-the-build-process"></a>Безопасность во время процесса сборки  
 Visual Studio автоматически настраивает параметры безопасности на компьютере разработчика, чтобы обеспечить предоставление решению доверия во время сборки. Это позволяет решению выполняться во время отладки.  
  
 Проекты Office используют сертификаты для проверки издателя. Visual Studio автоматически создает временный сертификат для идентификации решений Office и настраивает на компьютере разработчика доверие к временному сертификату.  
  
 Для получения дополнительной информации см. [Securing Office Solutions](../vsto/securing-office-solutions.md).  
  
### <a name="network-projects"></a>Сетевые проекты  
 Если сборка или документ расположены в сетевой папке, обновления локальной политики безопасности (на уровне пользователя) недостаточно для запуска решения. Администратор должен предоставить полное доверие на уровне компьютера к документам и сборкам, находящимся в сетевой папке, перед запуском решения. Дополнительные сведения о настройке политики безопасности см. в разделе [Securing Office Solutions](../vsto/securing-office-solutions.md).  
  
 Для проектов уровня документа необходимо также добавить полный путь к расположению документа в список надежных папок Office. Для получения дополнительной информации см. [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
## <a name="changing-the-platform-target"></a>Изменение целевой платформы  
 Целевой платформой по умолчанию для проектов Office является **Любой ЦП**. Этот параметр обычно не следует изменять. Решения Office, собранные с параметром целевой платформы **Любой ЦП** , выполняются в 32- и 64-разрядных версиях Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] или [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
 Целевую платформу x64 следует задавать, если вы создаете решение, которое будет выполняться только в 64-разрядных версиях Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] или [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]и вызывать встроенные 64 разрядные интерфейсы API. Дополнительные сведения об изменении целевой платформы см. в разделе [как: Настройка проекта для конкретной платформы](../ide/how-to-configure-projects-to-target-platforms.md).  
  
 Если задана целевая платформа x64, решение не будет запускаться в 32-разрядных версиях Windows или Office. Если в качестве целевой платформы используется процессор x64, решение должно выполняться в 64-разрядном процессе.  
  
## <a name="using-the-clean-command"></a>Использование команды очистки  
 Для удаления файлов, созданных при сборке проекта, с компьютера разработчика можно использовать команду **Очистить** в меню **Сборка** среды [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Команда **Очистить** удаляет все файлы в каталоге выходных файлов сборки. Для проектов на уровне приложения команда **Очистить** также удаляет записи реестра, созданные в процессе сборки.  
  
## <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Отладка проектов Office](../vsto/debugging-office-projects.md)|Описываются проблемы, которые могут возникать при отладке проектов Office.|  
|[Пошаговое руководство. Создание первой настройки на уровне документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Содержит сведения о создании базовой настройки на уровне документа для Excel.|  
|[Практическое руководство. Повторное включение надстройки VSTO, которая была отключена](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Описывается повторное включение надстройки VSTO, которая была отключена аппаратным или программным образом.|  
|[Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)|Содержит ссылки на сведения о создании решений Office и о роли сборок в решении.|  
  
  