---
title: Create UML modeling projects and diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5884dcd3f9e3cb8f1910d2e23ec80f910ed2fc9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301000"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Создание проектов и схем моделирования UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Модели UML помогают понять, обсудить и спроектировать системы программного обеспечения. Visual Studio предоставляет шаблоны для пяти наиболее часто используемых схем UML: действия, класса, компонента, последовательности и варианта использования. В дополнение, можно создавать схемы слоев, которые помогают определить структуру системы.

 Схемы моделирования UML и схемы слоев могут существовать только внутри проекта моделирования. Каждый проект моделирования содержит совместную модель UML и несколько схем UML. Каждая схема представляет собой частичный вид модели. Модель UML содержит все элементы схем UML, при этом ее можно открыть при помощи Обозревателя модели UML. For information about models and their relationship to diagrams, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md). For information about modeling projects under version control, see [Manage models and diagrams under version control](../modeling/manage-models-and-diagrams-under-version-control.md) and [Structure your modeling solution](../modeling/structure-your-modeling-solution.md)

> [!NOTE]
> Существует другой вид схемы, схема класса .NET, которая используется для визуализации программного кода. For more information, see [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="CreatingModelingDiagrams"></a> Create a Diagram in a Modeling Project
 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Создание схемы и добавление ее в проект

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. In the **Add New Diagram** dialog box, click the type of modeling diagram that you want.

    ![Add New Diagram dialog](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. Введите имя для новой схемы.

4. In the **Add to modeling project** box:

   - Select a modeling project that already exists in your solution, and then click **OK**.

     \- или -

   1. Select **Create a new modeling project**, and then click **OK**.

   2. In the **Create New Modeling Project** dialog box, type a name and location for the new project, and then click **OK**.

        ![Create New Modeling Project dialog](../modeling/media/uml-createmodel.png "UML_CreateModel")

        Если решение уже открыто, то новый проект будет добавлен в решение. Если открытого решения нет, то можно ввести имя нового решения.

   Если проект моделирования уже существует, можно также использовать следующую процедуру.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Добавление схемы в существующий проект моделирования

1. In **Solution Explorer**, click the modeling project node.

    > [!NOTE]
    > The modeling project contains a model definition folder named **ModelDefinition**.

2. В меню **Проект** выберите пункт **Добавить новый элемент**.

3. In the **Add New Item -** *\<project name>* dialog box, under **Templates**, click the modeling diagram type, for example, **UML Component Diagram**.

4. Type a name for the diagram, and then click **Add**.

     Схема моделирования откроется и появится в проекте моделирования.

    > [!CAUTION]
    > Не следует добавлять, копировать или перетаскивать файлы существующей схемы в другие проекты моделирования или в другие местоположения в решении. Из-за этого могут исчезнуть элементы из скопированных схем или могут возникнуть ошибки при открытии схем. Файл схемы необходимо открывать из проекта моделирования, в котором она была создана. Это обусловлено тем, что схема UML является видом модели, принадлежащей ее проекту моделирования. Чтобы скопировать файл схемы, создайте новую схему, затем скопируйте элементы из схемы-источника в новую схему. For more information, see [Troubleshooting Modeling Projects and Diagrams](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>Создание пустого проекта моделирования

1. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

2. In the **New Project** dialog box, under **Installed Templates**, click **Modeling Projects**.

3. In the middle window, click **Modeling Project**.

4. Name the project and specify a location in the **Name** and **Location** boxes.

5. In the **Solution** box, select **Add to Solution** to add the new project to a solution you already have open; or **Create new Solution** to close any open solution and add the project to a new solution.

## <a name="RemovingModelingDiagrams"></a> Removing Modeling Diagrams from a Project
 Можно полностью удалить схему или временно исключить ее из проекта, а затем восстановить.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Полное удаление схемы из проекта

- In **Solution Explorer**, right-click the main file that represents the diagram, and then click **Delete**.

     Схема удаляется из проекта и из файловой системы. The elements shown on the diagram are not removed from **UML Model Explorer**.

    > [!NOTE]
    > У каждой схемы есть два файла, при этом один является вспомогательным. Например, если создана схема компонентов с именем `CD1`, то надо удалить файл с именем `CD1.componentdiagram`. Его вспомогательный файл с именем `CD1.componentdiagram.layout` удалится автоматически.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Временное исключение схемы из проекта

- In **Solution Explorer**, right-click the diagram file, and then click **Exclude from Project**.

     Схема удаляется из проекта. Она не удаляется из файловой системы.

    > [!NOTE]
    > The elements shown on the diagram are not removed from **UML Model Explorer**.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Восстановление временно исключенной схемы из проекта

1. In **Solution Explorer**, click the modeling project node.

    > [!NOTE]
    > The modeling project contains a model definition folder named **ModelDefinition**.

2. On the **Project** menu, click **Add Existing Item**.

3. In the **Add Existing Item** dialog box, locate the diagram file, select the file, and then click **Add**.

     Схема моделирования откроется и появится в проекте моделирования.

    > [!NOTE]
    > Каждая схема имеет пару файлов в файловой системе. Не выбирайте файл с расширением `.layout`. Visual Studio не поддерживает также добавление существующих схем UML в несколько проектов моделирования. Каждый файл схемы должен открываться только в том проекте моделирования, в котором он был создан. Это обусловлено тем, что схема UML является видом модели, принадлежащей ее проекту моделирования.

## <a name="NonModelDiagrams"></a> Diagrams that Do Not Require Modeling Projects
 Следующие виды схем не являются частью проекта моделирования.

- Схемы классов, которые создаются в качестве видов исходного кода. Они не связаны с схемами класса UML. For more information, see [Designing and Viewing Classes and Types](../ide/designing-and-viewing-classes-and-types.md).

- Карты кода. См. раздел [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

- Схемы, которые не относятся к схемам UML или схемам слоев, таким как доменные языки.

## <a name="TroubleshootingModelingProjects"></a> Troubleshooting Modeling Projects and Diagrams
 В следующей таблице описываются проблемы, которые могут возникать в проектах моделирования или в схемах, и способы их устранения.

|**Проблема**|**Causes**|**Решение**|
|---------------|----------------|--------------------|
|Проект моделирования не получается открыть или загрузить в решение.<br /><br /> Отображается следующее сообщение:<br /><br /> "Один или несколько проектов в решении были загружены неправильно. Дополнительную информацию см. в окне вывода."<br /><br /> Окно вывода отображает следующее сообщение:<br /><br /> "*ModelingProjectFilenameAndPath*.modelproj: error: Unrecognized Guid format."|У проекта моделирования есть ссылки на проекты с одинаковым именем и в одном решении.<br /><br /> Например, слой связан с проектами с одинаковым именем и в одном решении.|Используйте текстовый редактор, чтобы открыть файл проекта моделирования, удалите ссылки, затем попытайтесь открыть проект моделирования снова.<br /><br /> Чтобы избежать проблем, не добавляйте ссылки на проекты с одинаковым именем. Убедитесь, что проекты имеют уникальные имена.|
|Отсутствуют элементы схемы, добавленные, скопированные или перемещенные в другой проект моделирования или в другие местоположения в решении.<br /><br /> -или-<br /><br /> Отображается следующее решение при попытке открытия схемы:<br /><br /> -   "Some shapes or connectors on the diagram are missing because their definitions do not exist in this project. Определения были удалены из модели в то время, как схема была закрыта, или схема была скопирована в другой проект, в котором такие определения отсутствуют."<br /><br /> -или-<br /><br /> -   "This document is opened by another project."|Файл схемы был добавлен, перемещен или скопирован из проекта моделирования в другой проект моделирования или в другое расположение в решении.|Чтобы скопировать файл схемы, создайте новую схему, затем скопируйте элементы из схемы-источника в новую схему.|

## <a name="see-also"></a>См. также раздел
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [Structure your modeling solution](../modeling/structure-your-modeling-solution.md)
