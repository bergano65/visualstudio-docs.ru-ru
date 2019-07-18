---
title: Создание пакета установщика Windows | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e92e965f0efe531f1618be509d0a7c9655c573d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682536"
---
# <a name="authoring-a-windows-installer-package"></a>Создание пакета установщика Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Диски с данными модели установщика Windows. Вместо того чтобы писать процедурный сценарий для копирования файлов и записи реестра, например, создаваемых строк и столбцов в таблицах базы данных, которые содержат данные файлов и реестра.  
  
## <a name="database-entries"></a>Записи базы данных  
 Чтобы установить пакет VSPackage, пакет установщика Windows должен содержать записи базы данных для выполнения следующих задач:  
  
- Поиск в системе обнаружения версий [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage поддерживает (с помощью установщика Windows таблицы, в которых AppSearch, CompLocator, RegLocator, DrLocator и подпись).  
  
- Отменить установку, если не поддерживаемая версия [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] установлен или если другой системы пакета VSPackage не требования (с помощью таблицы LaunchCondition).  
  
- Установите пакет VSPackage и зависимые файлы (с помощью каталога, компонентов и таблицы файлов).  
  
- Добавьте соответствующую информацию для VSPackage в реестр (с использованием таблицы реестра).  
  
- Интеграция VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] путем вызова **/Setup для devenv.exe** (с помощью таблицы CustomAction).  
  
  Дополнительные сведения см. в разделе [установщика Windows](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Средства установки и настройки  
 Широкий набор средств установки стороннего предоставляют среду разработки для пакетов установщика Windows. Ниже перечислены два бесплатных средства.  
  
- InstallShield Limited Edition  
  
   Ограниченной версии InstallShield можно получить с помощью Visual Studio **новый проект** диалоговое окно. Разверните **другие типы проектов** , а затем выберите **установки и развертывания**. Выберите шаблон, InstallShield.  
  
- Набор инструментов XML установщика Windows  
  
   Набор инструментов построения пакетов установщика Windows из исходных файлов XML. Набор инструментов — это проект открытым кодом Майкрософт. Вы можете скачать исходный код и исполняемые файлы из [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
  Для коммерческих продуктов, которые интегрируют в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] с помощью [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], см. в разделе [ https://marketplace.visualstudio.com/ ](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>См. также  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
