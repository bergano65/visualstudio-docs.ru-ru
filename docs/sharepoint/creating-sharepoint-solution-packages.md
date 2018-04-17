---
title: Создание пакетов решений SharePoint | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e67073d1a12a9412b153adc0c06471c4d39ff15a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="creating-sharepoint-solution-packages"></a>Создание пакетов решений SharePoint
  С помощью конструктора пакетов, можно создавать и настраивать пакеты развертывания. Например можно добавить элементы проекта SharePoint и компонентов, сбрасывать сервер IIS, задавать области активации компонентов и указывать зависимости компонентов. Конструктор также создает манифест, в XML-файл с описанием каждого пакета.  
  
## <a name="packaging-tools"></a>Средства упаковки  
 Можно использовать **конструктора пакетов** для настройки пакета и создания манифеста. Можно добавлять элементы проектов SharePoint, настроить ли веб-сервера следует сбросить и настроить тип сервера развертывания. Дополнительные сведения см. в разделе [как: Добавление и удаление компонентов и элементов в пакете с помощью конструктора пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Кроме того, можно использовать **обозреватель пакетов** изменить компоненты и элементы в файл пакета (.wsp). Дополнительные сведения см. в разделе [как: Добавление и удаление компонентов и элементов в пакете с помощью обозревателя пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Можно использовать Visual Studio и MSBuild для создания файлов пакета (.wsp) для развертывания решения SharePoint. Этот процесс создает файлы манифестов, необходимые для развертывания SharePoint. Дополнительные сведения см. в разделе [как: Создание пакета SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b) и [как: Создание пакета решения SharePoint с помощью задач MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Параметры конструктора пакетов  
 Следующая таблица показывает свойства, которые можно настраивать пакетов SharePoint с **конструктора пакетов**.  
  
|Свойство конструктора пакетов|Описание значения по умолчанию|  
|-------------------------------|------------------------------------|  
|name|Обязательно. Имя пакета по умолчанию равно *ProjectName*.|  
|Сброс веб-сервера|Необязательный. Выберите, чтобы перезапустить веб-сервера после установки WSP-файл на сервере SharePoint.|  
|Тип сервера развертывания|Обязательно. Область по умолчанию имеет значение ApplicationServer.<br /><br /> ApplicationServer: Описание сервера, на котором размещены службы.<br /><br /> WebFrontEnd: Описание сервера, на котором размещается веб-сайтов.|  
|Элементы в решении|Все элементы проекта SharePoint и компонентов, которые могут быть добавлены в пакет.|  
|Элементы в пакете|Необязательный. Все элементы SharePoint и компонентов, которые вы хотите развернуть пакет.|  
  
## <a name="configuring-the-packaging-process"></a>Настройка обработки пакетов  
 После разработки решений SharePoint в Visual Studio можно настроить как пакеты для развертывания проектов.  
  
 В следующей таблице показаны два целевых объектов MSBuild, которые можно использовать для настройки способа создания WSP-файл.  
  
|целевого объекта|Описание|  
|------------|-----------------|  
|BeforeLayout|Целевой объект, который выполняет задачи, непосредственно перед файлы копируются в промежуточный каталог. Можно изменять файлы, прежде чем создавать файл пакета (.wsp).|  
|AfterLayout|Целевой объект, который выполняет задачи сразу после копирования в промежуточный каталог.|  
  
 Для получения дополнительной информации [как: Настройка пакета решения SharePoint с помощью целевых объектов MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Архитектура пакетов  
 При создании пакета SharePoint (WSP-файл) в Visual Studio, выполняются следующие действия.  
  
1.  Чтобы убедиться в правильности физической и семантической структуры пакета проверки компонентов и пакетов.  
  
2.  Перечисляются функции, элементы проекта и файлы пакета в пакете. Файлы манифестов для пакетов и компонентов, преобразуются в включают все сведения, необходимые для развертывания и активации. Токены заменяются полными значениями.  
  
3.  Настраиваемые цели BeforeLayout MSBuild выполняется. Можно создать этот шаг, чтобы вносить пользовательские изменения в пакет перед созданием WSP-файл.  
  
4.  Перечислимый файлы копируются в промежуточный каталог.  
  
5.  Настраиваемые цели AfterLayout MSBuild выполняется. Можно создать этот шаг, чтобы вносить пользовательские изменения в пакет перед созданием WSP-файл.  
  
6.  Файлы в промежуточном каталоге, которые добавляются в WSP-файл.  
  
## <a name="package-folder-structure"></a>Структура папок пакета  
 При создании пакета проекта SharePoint, WSP-файл создается в SolutionFolder\bin\\*BuildConfiguration* папки. Например, если решение находится в *диск*: \Visual Studio 2013\Projects\ListDefinition1 и конфигурацию построения задано значение выпуска, WSP-файл находится в *диск*: \Visual Studio 2013\ Projects\ListDefinition1\bin\Release.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Как: Добавление и удаление компонентов и элементов в пакете с помощью конструктора пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Как: Создание пакета SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [Как: Создание пакета решения SharePoint с помощью задач MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Практическое руководство. Настройка пакета решения SharePoint с помощью целевых объектов MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
  