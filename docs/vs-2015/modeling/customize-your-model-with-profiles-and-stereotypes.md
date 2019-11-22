---
title: Customize your model with profiles and stereotypes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b634b11418ef2d4220dc4eb07c825b514ab5494c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301193"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Настройка модели с помощью профилей и стереотипов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio стандартные элементы модели UML, например классы и компоненты, можно адаптировать для определенных целей. You can apply a *stereotype* to a model element that can change the element's list of properties. Stereotypes are defined within collections called *profiles*.

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Чтобы использовать стереотип, нужно пакет с профилем. Это позволит применить стереотипы, определенные в профиле, к элементам пакета. В Visual Studio уже включено несколько профилей. Кроме этого, можно определять собственные профили.

 Стереотипы можно устанавливать в списке свойств элемента. Для основных видов фигур на схеме примененные стереотипы отображаются и на фигуре, как показано в примере.

 ![A UML class with a stereotype.](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")

> [!NOTE]
> Если создать модель с помощью профиля, а затем отправить кому-либо эту модель, получатель не сможет видеть стереотипы, если на его компьютере не установлен тот же профиль.

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Добавление стереотипов к элементам модели UML](../modeling/add-stereotypes-to-uml-model-elements.md)|Размещение элемента модели в пакете, связывание пакета с профилем и применение стереотипа к элементу.|
|[Стандартные стереотипы для моделей UML](../modeling/standard-stereotypes-for-uml-models.md)|Стандартные профили UML L2 и L3 устанавливаются вместе с Visual Studio, и все модели связаны с ними по умолчанию. Они предоставляют стереотипы для создания заметок к моделям.<br /><br /> Например, применив к классу стереотип Specification, можно указать, что он позволяет настраивать поведение только тех его экземпляров, которые видно извне.|
|[Определение профиля для расширения UML](../modeling/define-a-profile-to-extend-uml.md)|Программа позволяет определять собственные стереотипы и средства, подходящие для вашего приложения.<br /><br /> Например, при разработке программного обеспечения для банка можно определить для применения к классам стереотип Account (Счет). Это позволит описывать различные типы счетов и их отношения, используя схемы классов.|
|[Установка профиля UML](../modeling/install-a-uml-profile.md)|Если кто-то предоставил вам UML-профиль, его можно установить на компьютере.|
|[Определение пользовательского элемента для панели элементов моделирования](../modeling/define-a-custom-modeling-toolbox-item.md)|Настраиваемый элемент панели элементов позволяет избежать постоянной установки стереотипа для новых элементов.|
