---
title: Средства работы с моделью EDM
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db58bb1826aab9a26dcec6a9475c49fc99057891
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661105"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Средства модели EDM в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Платформа Entity Framework — это технология объектно реляционного сопоставления, который позволяет разработчикам .NET работать с реляционными данными с помощью специфических для домена объектов. Это устраняет необходимость в большей части кода для доступа к данным, который разработчикам обычно приходится писать. Entity Framework является рекомендуемые объектно реляционного сопоставления (ORM), моделирование технологии для новых приложений .NET.

 По состоянию на март 2016 г., является самой последней версии [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Платформа Entity Framework 7](https://docs.efproject.net/en/latest/) в предварительной версии.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Инструменты предназначены для построения [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] приложений. Полная документация по [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] инструменты — здесь: [Платформа Entity Framework](https://msdn.microsoft.com/data/jj590134).

 С помощью [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] средства, можно создать *концептуальной модели* из существующей базы данных графически визуализировать и внести нужные изменения. Либо можно сначала создать концептуальную модель с помощью графических средств, а затем создать базу данных, которая поддерживает эту модель. В любом случае можно автоматически обновлять модель при изменении основной базы данных и автоматически создавать код объектного уровня для приложения. Процессы создания базы данных и создания кода объектного уровня допускают настройку.

 Ниже приведены конкретные средства, входящие в состав средств модели EDM в Visual Studio 2015.

- Можно использовать [!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] конструктор** (**конструктор сущностей**) можно визуально создавать и изменять сущности, ассоциации, сопоставления и связи наследования. **Конструктор сущностей** также создает [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] или [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] кода уровня объекта.

- Можно использовать  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] мастер** для создания концептуальной модели из существующей базы данных и добавить подключение к базе данных в приложение.

- Можно использовать **мастер создания базы данных** чтобы сначала создать концептуальную модель, а затем создать базу данных, поддерживающую модель.

- Можно использовать **мастер обновления моделей** для обновления вашей концептуальную модель, модель хранения и сопоставления, когда были внесены изменения в основную базу данных.

  > [!NOTE]
  >  Начиная с Visual Studio 2010, [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] средства не поддерживают [!INCLUDE[ss2k](../includes/ss2k-md.md)].

  Средства позволяют создать или изменить EDMX-файла. Этот файл содержит сведения, описывающие концептуальной модели, модели хранения и сопоставления между ними. Дополнительные сведения см. в разделе [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools позволяют создавать приложения, использующие модели EDM. Средства можно сформировать концептуальную модель, проверить существующую модель, подготовить файлы исходного кода, которые содержат классы объектов на основе концептуальной модели и создать файлы исходного кода, содержащие представления, создаваемые модели. Подробные сведения см. в разделе [Pre-Generated сопоставления представлений](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Описывает использование [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] средств, который [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] предоставляет для создания приложений.|
|[Сущностная модель данных](http://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Предоставляет ссылки и сведения для работы с данными, используемый приложений на платформе [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|
|[Приступая к работе на полной .NET (консоль, WinForms, WPF, и т.д.)](/ef/ef6/get-started)|Предоставляет учебники по созданию классических приложений .NET, использующих Entity Framework 7.|
|[ASP.NET 5 приложения в новую базу данных](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|В этой статье описывается создание нового приложения ASP.NET 5 с помощью Entity Framework 7.|

## <a name="see-also"></a>См. также
 [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
