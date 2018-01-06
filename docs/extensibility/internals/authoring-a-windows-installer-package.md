---
title: "Создание пакета установщика Windows | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2055f57e78c348f3f8e53187126588f382f0b944
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="authoring-a-windows-installer-package"></a>Создание пакета установщика Windows
Установщик Windows модели дисках с данными. Вместо того чтобы писать процедурных скрипта для копирования файлов и запись реестра, например, можно создавать строки и столбцы в таблицах базы данных, которые содержат данные файлов и реестра.  
  
## <a name="database-entries"></a>Записи базы данных  
 Чтобы установить пакет VSPackage, пакет установщика Windows должен содержать записи базы данных для выполнения следующих задач:  
  
-   Найти систему, чтобы найти версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage поддерживает (с помощью таблицы установщика Windows, включая AppSearch, CompLocator, RegLocator, DrLocator и подпись).  
  
-   Отменить установку, если ни одна из поддерживаемых версий [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установлен или если другой системе, предъявляемым VSPackage не выполняется (с использованием таблицы LaunchCondition).  
  
-   Установите пакет VSPackage и зависимые файлы (с помощью каталога, компонент и таблицы файлов).  
  
-   Добавьте соответствующую информацию для VSPackage в реестр (с помощью таблицы реестра).  
  
-   Интеграции VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] путем вызова **/Setup devenv.exe** (с помощью таблицы настраиваемое действие).  
  
 Дополнительные сведения см. в разделе [установщика Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Средства установки и настройки  
 Различные установки стороннего средства предоставляют среду разработки для пакетов установщика Windows. Ниже перечислены два бесплатных средств.  
  
-   InstallShield Limited Edition  
  
     Является ограниченной версией InstallShield можно получить с помощью Visual Studio **новый проект** диалогового окна. Разверните **другие типы проектов** , а затем выберите **Установка и развертывание**. Выберите шаблон InstallShield.  
  
-   Набор инструментов XML установщика Windows  
  
     Набор средств построения пакетов установщика Windows из исходного XML-файлов. Набор инструментов является открытым исходным кодом Microsoft project. Можно загрузить исходный код и исполняемых файлов на основе [http://sourceforge.net/projects/wix](http://sourceforge.net/projects/wix).  
  
 Для коммерческих продуктов, которые интегрируют в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], в разделе [http://visualstudiogallery.com](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>См. также  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)