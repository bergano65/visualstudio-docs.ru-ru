---
title: Практическое руководство. Перенос доменного языка в новую версию
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2f4051f0771d4343ee09593a2e9674fa904a5f85
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Практическое руководство. Перенос доменного языка в новую версию
Можно перенести проекты, которые определяют и используют доменного языка для [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] версии [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , включенного в состав [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].

 Средство миграции предоставляется как часть [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. Средство преобразует [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проекты и решения, использующие или определить инструменты DSL.

 Необходимо запустить средство миграции явным образом: оно не запускается автоматически при открытии решения в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Инструментов и документов подробные инструкции можно найти по этому пути:

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Перед переносе проектов DSL
 Средство миграции изменяет [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] файлы проекта (**.csproj**) и файлы решений (**.sln**).

#### <a name="to-prepare-projects-for-migration"></a>Для подготовки к миграции проектов.

-   Убедитесь, что **.csproj** и **.sln** файлы могут быть записаны. Если они находятся в системе управления версиями, убедитесь, что они будут извлечены.

-   Создайте копию папки, которые планируется перенести.

## <a name="migrating-a-collection-of-projects"></a>Миграция коллекций проектов

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Чтобы перенести DSL проекты и решения Visual Studio 2010

1.  Запустите средство миграции DSL.

    -   Дважды щелкните средство в проводнике Windows (или File Explorer) или запустить средство из командной строки. Средство — в этом расположении:

         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2.  Выберите папку, содержащую решения и проекты, которые нужно преобразовать.

    -   Введите путь в поле в верхней части инструмента, или нажмите кнопку **Обзор**.

     Средство миграции дерево проектов, которые определяют или использовать доменного языка. Дерево включает каждого проекта, использующего **Microsoft.VisualStudio.Modeling.Sdk** или **TextTemplating** сборки.

3.  Просмотр дерева проектов и снимите проекты, которые нужно преобразовать.

    -   Выберите проект или решение, чтобы увидеть список изменений, которые позволят средство.

        > [!NOTE]
        >  Флажки, которые появляются рядом с имена папок не действуют. Необходимо развернуть папки для проверки проектов и решений.

4.  Преобразуйте проекты.

    1.  Нажмите кнопку **преобразовать**.

         До преобразования каждого файла проекта, копия *проекта *** .csproj** сохраняется как *проекта ***.vs2008.csproj**

         Каждая копия *решения *** .sln** сохраняется как *решения ***.vs2008.sln**

    2.  Проверьте все неудачные преобразования, включенные в отчет.

         Сбоев выводятся в текстовом окне. Кроме того в представлении дерева отображается красного флажка на каждом узле, который не удалось преобразовать. Можно щелкнуть узел, чтобы получить дополнительные сведения об этой ошибке.

5.  **Преобразовать все шаблоны** в решениях, содержащий успешно преобразования проектов.

    1.  Откройте решение.

    2.  Нажмите кнопку **преобразовать все шаблоны** кнопку в заголовке обозревателя решений.

        > [!NOTE]
        >  Этот шаг можно сделать ненужные. Дополнительные сведения см. в разделе [как автоматизировать преобразовать все шаблоны](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6.  Обновите пользовательский код в преобразованные проекты.

    -   Попытка построить проекты и изучения каких-либо ошибок.

    -   Проверьте конструктор.


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>См. также

- [Связанные сообщения в блогах](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)