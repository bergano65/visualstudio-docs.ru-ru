---
title: "Создание пакета установщика Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSI-файлы, пакеты VSPackage"
  - "MSI-файлы, пакеты VSPackage"
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Создание пакета установщика Windows
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Установщик Windows модели дисков с данными. Вместо написания процедурный сценарий для копирования файлов и записи реестра, например, можно создать строки и столбцы в таблицах базы данных, содержащих данные файлов и реестра.  
  
## Записи базы данных  
 Чтобы установить VSPackage, пакет установщика Windows должен содержать записи базы данных для выполнения следующих задач:  
  
-   Поиск систему, чтобы найти версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage поддерживает \(с помощью таблицы установщика Windows, включая AppSearch, CompLocator, RegLocator, DrLocator и подпись\).  
  
-   Отменить установку, если ни одна из поддерживаемых версий [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установлен или если не выполняется еще одна отличительная VSPackage системы \(с использованием таблицы LaunchCondition\).  
  
-   Установите VSPackage и зависимые файлы \(с помощью каталога, компонентов и таблицы файлов\).  
  
-   Добавьте соответствующую информацию для VSPackage реестра \(с помощью таблиц реестра\).  
  
-   Интегрировать пакет VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] путем вызова **devenv.exe \/setup** \(с помощью таблицы CustomAction\).  
  
 Дополнительные сведения см. в разделе [установщика Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## Средства установки и настройки  
 Различные средства установки стороннего предоставляют среду разработки для пакетов установщика Windows. Два бесплатных средств таковы:  
  
-   InstallShield Limited Edition  
  
     Ограниченная версия InstallShield можно получить с помощью Visual Studio **Новый проект** диалогового окна. Разверните **другие типы проектов** а затем выберите **установки и развертывания**. Выберите шаблон InstallShield.  
  
-   Набор инструментов XML установщика Windows  
  
     Набор инструментов построения пакетов установщика Windows из исходных файлов XML. Набор инструментов — это Microsoft открытый проект. Можно загрузить исходный код и исполняемые файлы в [http:\/\/sourceforge.net\/projects\/wix](http://sourceforge.net/projects/wix).  
  
 Для коммерческих продуктов, которые интегрируют в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], в разделе [http:\/\/visualstudiogallery.com](http://visualstudiogallery.com/).  
  
## См. также  
 [Установка пакетов VSPackages с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)