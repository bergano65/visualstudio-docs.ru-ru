---
title: Общие сведения о модели автоматизации | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ea38dc79bd557f17bbae8276dd112304c9a40fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186734"
---
# <a name="automation-model-overview"></a>Общие сведения о модели автоматизации
Модель автоматизации состоит из набора объектов, с которыми можно создать надстройку или расширение Visual Studio. Надстройка — это приложение, которое может управлять средой Visual Studio и автоматизировать общие задачи. Расширение Visual Studio может создавать пользовательские компоненты Visual Studio или добавлять к функциональным возможностям стандартных компонентов, таких как текстовый редактор.

## <a name="objects-in-the-automation-model"></a>Объекты в модели автоматизации
 Модель автоматизации состоит из связанных групп объектов, которые управляют основными аспектами общей среды. На следующей диаграмме показан обширный набор объектов Visual Studio, образующих модель автоматизации.

 ![Диаграмма объектов автоматизации Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "всвисуалстудиоаутоматионобжектчарт")

 Дополнительные сведения см. [в разделе Расширение среды Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 Среда предоставляет модель для различных функциональных областей. Например, существует модель кода для различных элементов, которые могут быть найдены в коде. Существует модель документа для различных элементов документа. Одна область, область проекта, является особым интересом к поставщикам VSPackage. Вам, вероятно, потребуется, чтобы новые типы проектов участвовали в модели автоматизации практически так же, как [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] вносят вклад в модель автоматизации. Этот процесс описан в статьи [предоставление автоматизации для пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).

 Места, где можно расдумать расширение модели автоматизации среды:

- Проект

- Document

- Код

- Построить

Дополнительные сведения об автоматизации см. в разделе [Автоматизация и расширяемость для Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Этот документ и содержащиеся в нем документы содержат ссылки на, которые помогут принять решение о том, как следует предоставлять автоматизацию для VSPackage.

## <a name="see-also"></a>См. также
- [Пошаговое руководство. Создание надстройки](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)