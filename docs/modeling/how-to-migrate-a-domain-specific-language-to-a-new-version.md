---
title: "Практическое руководство: перенос доменного языка на новую версию | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 14
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 397efd1049ea52b2e7c67a46509d2a088c6fa488
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Практическое руководство. Перенос доменного языка в новую версию
Можно выполнить перенос проектов, определения и использования доменного языка для [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] версии [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , включенного в состав [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 Средство миграции предоставляется как часть [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. Средство преобразует [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проекты и решения, использующие или определения DSL Tools.  
  
 Необходимо запустить средство переноса явным образом: оно не запускается автоматически при открытии решения в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Инструментов и документов подробные инструкции можно найти по этому пути:  
  
 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>До миграции проекты DSL  
 Средство миграции изменяет [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] файлов проекта (**.csproj**) и файлы решений (**.sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>Подготовка проектов к миграции.  
  
-   Убедитесь, что **.csproj** и **.sln** файлы могут быть записаны. Если они находятся в системе управления версиями, убедитесь, что они извлечены.  
  
-   Создайте копию папки, которые требуется перенести.  
  
## <a name="migrating-a-collection-of-projects"></a>Перенос коллекции проектов  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Чтобы перенести DSL проектов и решений в Visual Studio 2010  
  
1.  Запустите средство миграции DSL.  
  
    -   Дважды щелкните инструмент в проводнике Windows (или проводника) или запустите средство из командной строки. Средство находится в этом месте:  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  Выберите папку, содержащую решения и проекты, которые требуется преобразовать.  
  
    -   Введите путь в поле в верхней части инструмента или щелкните **Обзор**.  
  
     Средство миграции дерево проектов, определять и использовать DSL. Дерево включает каждого проекта, использующего **Microsoft.VisualStudio.Modeling.Sdk** или **TextTemplating** сборки.  
  
3.  Просмотр дерева проектов и снимите флажки проектов, которые не требуется преобразовать.  
  
    -   Выберите проект или решение, чтобы увидеть список изменений, делают средства.  
  
        > [!NOTE]
        >  Флажки, которые появляются рядом с имена папок не оказывают влияния. Необходимо развернуть папки для проверки проектов и решений.  
  
4.  Преобразование проектов.  
  
    1.  Щелкните **преобразовать**.  
  
         Прежде чем преобразовать каждый файл проекта, копии *проекта***.csproj** сохраняется как *проекта***. vs2008.csproj**  
  
         Копия каждого *решение***.sln** сохраняется как *решение***. vs2008.sln**  
  
    2.  Проанализируйте сбой преобразования, которые сообщаются.  
  
         Ошибки выводятся в текстовом окне. Кроме того в представлении дерева отображается красный флаг на каждом узле, который не удалось преобразовать. Можно щелкнуть узел, чтобы получить дополнительные сведения об этой ошибке.  
  
5.  **Преобразовать все шаблоны** в решениях, содержащий успешно преобразования проектов.  
  
    1.  Откройте решение.  
  
    2.  Щелкните **преобразовать все шаблоны** кнопку в заголовке обозревателя решений.  
  
        > [!NOTE]
        >  Это можно сделать ненужные. Дополнительные сведения см. в разделе [как автоматизировать преобразовать все шаблоны](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6.  Обновите пользовательский код преобразованные проекты.  
  
    -   Попытка построить проекты и проверьте наличие ошибок.  
  
    -   Тестирование в конструктор.  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>См. также  
 [Связанные сообщения в блогах](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)


