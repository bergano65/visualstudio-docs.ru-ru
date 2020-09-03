---
title: Решения Visio
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a79b3c9964a24daf0a12ab90f47fb5903d89cdd0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985508"
---
# <a name="visio-solutions"></a>Решения Visio
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office Visio. Надстройки VSTO можно использовать для автоматизации Visio, расширения функциональных возможностей этого продукта и настройки его пользовательского интерфейса.

 Дополнительные сведения о надстройках VSTO см. в статье Приступая к [программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md). Если вы не знакомы с программированием с Microsoft Office, см. статью Приступая к [работе &#40;разработке решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 **Применимость.** Информация в этой статье относится к проектам надстроек VSTO для Visio 2010. Для получения дополнительной информации см. [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Автоматизация Visio с помощью объектной модели Visio
 Объектная модель Visio предоставляет различные классы, которые можно использовать для автоматизации Visio с целью создания диаграмм для организационных диаграмм, блок-схем, временных шкал проекта, сетевых диаграмм, пространств Office и проч. Интерфейс API позволяет написать код для выполнения общих задач.

- Конструирование и размещение фигур и текста в диаграммах.

- Управление поведением фигур с учетом бизнес-логики и данных, вводимых пользователем.

- Управление отображением диаграмм, например панорамированием и масштабированием.

- Настройка пользовательского интерфейса приложения.

- Импортируйте внешние данные в Visio, свяжите их с фигурами и отобразите в графическом виде на странице.

  Пошаговые процедуры и примеры кода для использования объектной модели Visio можно использовать для работы с документами и фигурами в [работе с документами Visio](../vsto/working-with-visio-documents.md) и [работы с фигурами Visio](../vsto/working-with-visio-shapes.md).

  Для доступа к объектной модели Visio из надстройки VSTO используйте поле `Application` класса `ThisAddIn` в своем проекте. Поле `Application` возвращает объект `Microsoft.Office.Interop.Visio.Application`, представляющий текущий экземпляр Visio. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

  При вызове объектной модели Visio используются типы, предоставляемые в основной сборке взаимодействия (PIA) для Visio. Основная сборка взаимодействия выступает в качестве моста между управляемым кодом в надстройке VSTO и объектной моделью COM в Visio. Все типы в основной сборке взаимодействия Visio определены в пространстве имен `Microsoft.Office.Interop.Visio`. Дополнительные сведения о первичных сборках взаимодействия см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) и [основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Общие сведения об объектной модели Visio
 Общие сведения об объектной модели Visio см. в статье [Общие сведения об](../vsto/visio-object-model-overview.md)объектной модели Visio, которая содержит ссылки на справочник по объектной модели Visio и пакеты SDK.

## <a name="customize-the-user-interface-of-visio"></a>Настройка пользовательского интерфейса Visio
 Пользовательский интерфейс Visio имеет следующие возможности настройки.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Настройка ленты.|[Обзор ленты](../vsto/ribbon-overview.md)|

 Сведения о настройке пользовательского интерфейса Visio см. в справочной документации по VBA для класса [Visio.UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>См. также раздел
- [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
- [Office - основные сборки взаимодействия](../vsto/office-primary-interop-assemblies.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Visio 2010 в разработке решений для Office](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
