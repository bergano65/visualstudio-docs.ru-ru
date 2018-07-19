---
title: Средства платформы Entity Framework в Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3209a79b0358471977a0e58e8ab5d8d7e5c08e07
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755372"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Средства платформы Entity Framework в Visual Studio
Платформа Entity Framework — это технология объектно реляционного сопоставления, который позволяет разработчикам .NET работать с реляционными данными с помощью специфических для домена объектов. Это устраняет необходимость в большей части кода для доступа к данным, который разработчикам обычно приходится писать. Entity Framework является рекомендуемые объектно реляционного сопоставления (ORM), моделирование технологии для новых приложений .NET.

Средства платформы Entity Framework предназначены для построения приложений Entity Framework (EF). Полная документация по Entity Framework находится здесь: [EF Core и EF 6](/ef/).

С помощью средства платформы Entity Framework, можно создавать *концептуальной модели* из существующей базы данных графически визуализировать и внести нужные изменения. Либо можно сначала создать концептуальную модель с помощью графических средств, а затем создать базу данных, которая поддерживает эту модель. В любом случае можно автоматически обновлять модель при изменении основной базы данных и автоматически создавать код объектного уровня для приложения. Процессы создания базы данных и создания кода объектного уровня допускают настройку.

Средства Entity Framework устанавливаются как часть **хранение и обработка данных** рабочей нагрузки в установщике Visual Studio. Их также можно установить как компонент indvidual под **пакеты SDK, библиотек и платформ** категории.

Ниже приведены конкретные средства, входящие в состав средства платформы Entity Framework в Visual Studio.

-   Можно использовать [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] конструктор** (**конструктор сущностей**) можно визуально создавать и изменять сущности, ассоциации, сопоставления и связи наследования. **Конструктор сущностей** также создает [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] или [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] кода уровня объекта.

-   Можно использовать  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] мастер** для создания концептуальной модели из существующей базы данных и добавить подключение к базе данных в приложение.

-   Можно использовать **мастер создания базы данных** чтобы сначала создать концептуальную модель, а затем создать базу данных, поддерживающую модель.

-   Можно использовать **мастер обновления моделей** для обновления вашей концептуальную модель, модель хранения и сопоставления, когда были внесены изменения в основную базу данных.

    > [!NOTE]
    >  Начиная с Visual Studio 2010, средства платформы Entity Framework не поддерживают [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Средства создают или изменяют *.edmx* файл. Это *.edmx* файл содержит сведения, описывающие концептуальной модели, модели хранения и сопоставления между ними. Дополнительные сведения см. в разделе [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) помогут вам создавать приложения с использованием модели EDM. Power tools можно создать концептуальную модель, проверить существующую модель, подготовить файлы исходного кода, которые содержат классы объектов на основе концептуальной модели и создать файлы исходного кода, содержащие представления, создаваемые модели. Подробные сведения см. в разделе [Pre-Generated сопоставления представлений](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>См. также

|Заголовок|Описание:|
|-----------|-----------------|
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|Описывает использование [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] средств, который [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] предоставляет для создания приложений.|
|[Сущностная модель данных](/dotnet/framework/data/adonet/entity-data-model)|Предоставляет ссылки и сведения для работы с данными, используемый приложений на платформе [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|
|[Документация по Entity Framework (EF))](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|Предоставляет индекс видео, руководства и дополнительные документацию, которая поможет вам максимально эффективно платформы Entity Framework.|
|[ASP.NET 5 приложения в новую базу данных](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|В этой статье описывается создание нового приложения ASP.NET 5 с помощью Entity Framework 7.|

## <a name="see-also"></a>См. также

- [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)