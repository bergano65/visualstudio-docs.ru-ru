---
title: Создание пакета установщик Windows | Документация Майкрософт
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
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301130"
---
# <a name="authoring-a-windows-installer-package"></a>Создание пакета установщика Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Данные установщик Windows модели. Вместо написания процедурного скрипта для копирования файлов и записи записей реестра, например, создаются строки и столбцы в таблицах базы данных, содержащих данные файлов и реестра.  
  
## <a name="database-entries"></a>Записи базы данных  
 Чтобы установить VSPackage, пакет установщик Windows должен содержать записи базы данных для выполнения следующих задач:  
  
- Выполните поиск в системе, чтобы найти версии [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] поддерживаемых VSPackage (с помощью установщик Windows таблиц, включающих Аппсеарч, Комплокатор, Реглокатор, Дрлокатор и Signature).  
  
- Отмените установку, если не установлена поддерживаемая версия [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или если не выполнено другое требование к системе VSPackage (с использованием таблицы Лаунчкондитион).  
  
- Установите пакет VSPackage и зависимые файлы (с помощью таблиц каталога, компонента и файлов).  
  
- Добавьте соответствующие сведения для пакета VSPackage в реестр (с помощью таблицы реестра).  
  
- Интегрируйте пакет VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], вызвав **devenv. exe/setup** (с помощью таблицы CustomAction).  
  
  Дополнительные сведения см. в разделе [установщик Windows](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Средства установки  
 Различные средства настройки сторонних разработчиков предоставляют среду разработки для установщик Windows пакетов. Ниже перечислены два бесплатных средства.  
  
- InstallShield Limited Edition  
  
   Вы можете получить ограниченную версию InstallShield с помощью диалогового окна **Новый проект** Visual Studio. Разверните узел **другие типы проектов** , а затем выберите **Установка и развертывание**. Выберите шаблон InstallShield.  
  
- Набор инструментов XML установщика Windows  
  
   Набор инструментов создает установщик Windows пакеты из исходных файлов XML. Набор инструментов — это проект Microsoft с открытым исходным кодом. Исходный код и исполняемые файлы можно загрузить из [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/).  
  
  Сведения о коммерческих продуктах, которые интегрируются в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] с помощью [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], см. в разделе [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>См. также  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
