---
title: Средства платформы Entity Framework в Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 906176ebf782a537dffad1deddb41c71739e8a5e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="entity-framework-tools-in-visual-studio"></a>Средства платформы Entity Framework в Visual Studio
Entity Framework — это технология объектно реляционного сопоставления, которая позволяет разработчикам .NET для работы с реляционными данными, с помощью специфических для домена объектов. Это устраняет необходимость в большей части кода для доступа к данным, который разработчикам обычно приходится писать. Entity Framework является рекомендуемые объектно реляционного сопоставления (ORM), моделирование технологии для новых приложений .NET.

Средства платформы Entity Framework предназначены для создания приложений Entity Framework (EF). Полная документация по Entity Framework находится здесь: [EF ядра и EF 6](/ef/).

С помощью средства платформы Entity Framework, можно создать *концептуальной модели* из существующей базы данных графически визуализации и изменения концептуальной модели. Либо можно сначала создать концептуальную модель с помощью графических средств, а затем создать базу данных, которая поддерживает эту модель. В любом случае можно автоматически обновлять модель при изменении основной базы данных и автоматически создавать код объектного уровня для приложения. Процессы создания базы данных и создания кода объектного уровня допускают настройку.

Средства платформы Entity Framework устанавливаются как часть **хранения и обработки данных** рабочей нагрузки в установщик Visual Studio. Их также можно устанавливать как компонент indvidual под **пакетов SDK, библиотек и платформ** категории.

Ниже перечислены средства, входящие в состав средств платформы Entity Framework в Visual Studio:

-   Можно использовать [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] конструктор** (**Entity Designer**) для визуального создания и изменения сущностей, ассоциации, сопоставления и отношения наследования. **Entity Designer** также приводит к возникновению ошибки [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] или [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] код уровня объекта.

-   Можно использовать  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] мастер** создать концептуальную модель из существующей базы данных и добавить сведения о подключении базы данных в приложение.

-   Можно использовать **мастер создания базы данных** сначала создать концептуальную модель, а затем создать базу данных, поддерживающий модель.

-   Можно использовать **мастер обновления моделей** для обновления вашей концептуальную модель, модель хранения и сопоставления при были внесены изменения в основной базе данных.

    > [!NOTE]
    >  Начиная с Visual Studio 2010, средства платформы Entity Framework не поддерживают [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Средства позволяют создать или изменить EDMX-файл. Это EDMX-файл содержит сведения, описывающие концептуальной модели, модели хранения и сопоставления между ними. Дополнительные сведения см. в разделе [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) построения приложений, использующих модели EDM. Power tools можно создать концептуальную модель, проверить существующую модель, подготовить файлы исходного кода, которые содержат классы объектов на основе концептуальной модели и создать файлы исходного кода, содержащие представления, создаваемые модели. Дополнительные сведения см. в разделе [Pre-Generated сопоставления представлений](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|Описывает использование [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] средств, который [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] предоставляет для создания приложений.|
|[Сущностная модель данных](/dotnet/framework/data/adonet/entity-data-model)|Содержит ссылки и сведения для работы с данными, которые используются приложениями, построенных на [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|
|[Документации по Entity Framework (EF))](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|Предоставляет индекс видеоролики, учебные материалы и дополнительно документацию, которая поможет вам наиболее Entity Framework.|
|[ASP.NET 5 приложения для новой базы данных](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|В этой статье описывается создание нового приложения ASP.NET 5 с помощью Entity Framework 7.|

## <a name="see-also"></a>См. также

- [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)