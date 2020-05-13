---
title: Обзор модели автоматизации (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710011"
---
# <a name="automation-model-overview"></a>Обзор модели автоматизации
Модель автоматизации состоит из набора объектов, на фоне которых можно написать надстройку или расширение Visual Studio. Надстройка — это приложение, которое может манипулировать средой Visual Studio и автоматизировать общие задачи. Расширение Visual Studio может создавать пользовательские компоненты Visual Studio или добавлять в функциональность стандартных компонентов, таких как текстовый редактор.

## <a name="objects-in-the-automation-model"></a>Объекты в модели автоматизации
 Модель автоматизации состоит из связанных групп объектов, которые управляют основными аспектами общей среды. На следующей диаграмме показан обширный набор объектов Visual Studio, которые составляют модель автоматизации.

 ![Диаграмма объектов автоматизации Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioАвтоматизацияОбъектЧартЧартЧарт")

 Для получения дополнительной информации [см.](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)

 Среда обеспечивает модель для различных функциональных областей. Например, существует модель кода для различных элементов, которые можно найти в коде. Существует модель документа для различных элементов документа. Одна из областей, область проекта, представляет особый интерес для поставщиков VSPackage. Скорее всего, вы хотите, чтобы ваши новые типы [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проектов вносили свой вклад в модель автоматизации так же, как и внедили в модель автоматизации. Этот процесс изложен в [Обеспечении автоматизации для VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Места, где можно рассмотреть вопрос о расширении модели автоматизации среды:

- Проект

- Документ

- Код

- Построение

Для получения дополнительной информации об автоматизации [см. Автоматизация и расширяемость для Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Этот документ и документы, на которые он ссылается, помогут вам принять решения о том, как обеспечить автоматизацию вашего VSPackage.

## <a name="see-also"></a>См. также
- [Как: Создать надстройку](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
