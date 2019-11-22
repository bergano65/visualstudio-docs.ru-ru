---
title: Integrate UML models with other models and tools | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: caecb85392170559a860a7dc334570880d6e76f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301468"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Интеграция моделей UML с другими моделями и средствами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Модели UML можно интегрировать с другими моделями и с доменными языками.

 Интеграцию моделей можно осуществлять следующими способами, написав код расширения для выполнения разнообразных функций:

 Присоедините ссылки из любого элемента на другие элементы, такие как файлы, или элементы в других моделях.
В элементе UML можно хранить ссылки на другие элементы UML, файлы или другие объекты путем кодирования их удостоверений в виде строк.

 Например, можно написать расширение, которое связывает любое действие UML (то есть элемент на схеме деятельности) с другой схемой деятельности. Когда пользователь дважды щелкает действие, открывается другая схема. Это позволяет пользователю обеспечить более подробное представление о действии.

 Существует два способа сохранения строк и других данных в любом элементе:

- **Stereotype properties.** Можно определить профиль UML, в котором определяется стереотип, добавляющий свойства в элемент UML указанных типов. For example, you could define a profile that adds a property named **MoreDetail** to a UML action. Можно написать код расширения, который сохраняет данные связей в действии, применяя стереотип к действию и затем сохраняя данные в свойстве.

   Стереотип и его свойства отображаются для пользователя в окне "Свойства".

   Чтобы развернуть это расширение, следует упаковать определение профиля и код расширения в одно расширение [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   For more information, see [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md).

   For a sample project in which a profile is deployed together with menu commands and gesture handlers, see [Sample: UML Profiles](https://go.microsoft.com/fwlink/?LinkID=213811).

- **References.** Набор строк можно присоединить к любому элементу UML. Можно написать код, который хранит данные, такие как имя файла или GUID другого элемента. Это можно сделать без задания дополнительных определений. Ссылки не отображаются непосредственно пользователю.

   For more information, see [Attach reference strings to UML model elements](../modeling/attach-reference-strings-to-uml-model-elements.md). For a sample, see [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813).

  Существует два способа кодирования ссылок на элементы модели:

- **GUID and Filename** of the target model element and the model that contains it, or a particular diagram that displays it.

   For an example, see [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813).

- **ModelBus References.** ModelBus — это платформа для создания и разрешения ссылок между моделями. Она включает в себя средство выбора ModelBus, позволяющее пользователю выбрать элемент в модели. Она также помогает пользователю разрешать ссылки, которые теряются из-за изменений в целевой модели.

   For more information, see [Integrating Models by using Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Распространите изменения из одной модели в другую.
  Например, можно синхронизировать имя элемента с именем связанной схемы, чтобы при изменении пользователем одного имени также изменялось и другое. Существует два механизма для реализации такой работы:

1. **VMSDK Rules** can be used to propagate changes inside the same model.

    For an example, see [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813).

2. **VMSDK Events** can be used to propagate changes outside the model – for example, to change the filename of a linked document, or to change an element in another model.

   For information about both these mechanisms, see [How to: Respond to Changes in a UML Model](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Drag elements to copy them from one model to another You can let the user create elements by dragging items onto a UML diagram. Созданный элемент необязательно должен быть копией исходного. Например, можно разрешить пользователю перетаскивать схему деятельности из обозревателя решений на другую схему деятельности для создания нового действия.

   For more information see [Define a gesture handler on a modeling diagram](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) and [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="samples"></a>Примеры
 Please see the code sample [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813). Пример позволяет перетащить файл на любой элемент UML и затем открыть этот файл двойным щелчком элемента. Например, можно связать схему деятельности с элементом варианта использования. Значок, который показывает наличие связей у элементов.

 В этом примере кода демонстрируются следующие методики:

- [Присоединение строк ссылок к элементам модели UML](../modeling/attach-reference-strings-to-uml-model-elements.md)

   Пример кода сохраняет пути к файлам и GUID элементов в строках ссылок, сопоставленных с элементом.

- Добавление декораторов в элементы UML. For general information about decorators, see [Customizing Text and Image Fields](../modeling/customizing-text-and-image-fields.md).

   В этом примере добавляется декоратор изображения для фигур UML.

- [Практическое руководство. Реагирование на изменения в UML-модели](../misc/how-to-respond-to-changes-in-a-uml-model.md)

   В примере показано, как определить правило, реагирующее на новые фигуры на схеме.

- [Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [Определение обработчика жестов на схеме моделирования](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)

   В примере показано, как обрабатывать элементы, перетаскиваемые из проводника Windows (или проводника), обозревателя решений и других элементов UML.

  For an example in which a UML model is be read by a DSL, see [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="see-also"></a>См. также раздел
 [Define a menu command on a modeling diagram](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Define a gesture handler on a modeling diagram](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md) [How to: Respond to Changes in a UML Model](../misc/how-to-respond-to-changes-in-a-uml-model.md) [Sample: UML Profiles](https://go.microsoft.com/fwlink/?LinkID=213811) [Link UML Elements to Diagrams or other Files](https://go.microsoft.com/fwlink/?LinkId=213813)
