---
title: Поставка отменить поддержку для дизайнеров (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699679"
---
# <a name="supply-undo-support-to-designers"></a>Поставка отменить поддержку для дизайнеров

Дизайнерам, как и редакторам, обычно необходимо поддерживать отменить операции, чтобы пользователи могли отменить свои последние изменения при изменении элемента кода.

Большинство дизайнеров, реализованных в Visual Studio, имеют поддержку «отменить» автоматически обеспечиваемую окружающей средой.

Проектные реализации, которые должны обеспечить поддержку функции отменить:

- Обеспечить отменить управление путем реализации абстрактного базового класса<xref:System.ComponentModel.Design.UndoEngine>

- Сохранение поставок и поддержка CodeDOM <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> путем внедрения и классов.

Для получения дополнительной информации о написании дизайнеров с помощью .NET Framework, [см.](/previous-versions/37899azc(v=vs.140))

Обеспечивает [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] инфраструктуру по умолчанию отменить:

- Предоставление отменить реализации <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> управления <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> через и классы.

- Поставка настойчивости и поддержки CodeDOM через по умолчанию <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> и <xref:System.ComponentModel.Design.IComponentChangeService> реализации.

## <a name="obtain-undo-support-automatically"></a>Получение автоматической поддержки отменить

Любой дизайнер, созданный в Visual Studio имеет автоматическую и полную поддержку отменить, если, дизайнер:

- Использует основанный <xref:System.Windows.Forms.Control> класс для своего пользовательского интерфейса.

- Использует стандартную систему генерации кода на основе CodeDOM и систему разбора для генерации и сохранения кода.

   Для получения дополнительной информации о работе с поддержкой Visual Studio CodeDOM [см.](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)

## <a name="when-to-use-explicit-designer-undo-support"></a>Когда использовать явную поддержку отменить конструктор
 Дизайнеры должны поставлять свои собственные отменить управления, если они используют графический пользовательский интерфейс, <xref:System.Windows.Forms.Control>называемый адаптер представления, кроме одного поставляется .

 Примером этого может быть создание продукта с веб-интерфейсграфического дизайна, а не .NET Framework основе графического интерфейса.

 В таких случаях, нужно будет зарегистрировать этот адаптер представления с visual Studio с помощью <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>, и обеспечить явное управление отменить.

 Дизайнеры должны предоставить CodeDOM и поддержку настойчивости, если они <xref:System.CodeDom> не используют модель генерации кода Visual Studio, предусмотренную в пространстве имен.

## <a name="undo-support-features-of-the-designer"></a>Отменить функции поддержки дизайнера
 Окружающая среда SDK обеспечивает по умолчанию реализации интерфейсов, необходимых <xref:System.Windows.Forms.Control> для обеспечения отменить поддержку, которая может быть использована дизайнерами не используя на основе классов для своих пользовательских интерфейсов или стандартной модели CodeDOM и настойчивости.

 Класс <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> происходит от класса .NET Framework, <xref:System.ComponentModel.Design.UndoEngine> используя <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> реализацию класса для управления отменить операции.

 Visual Studio предоставляет следующую функцию для дизайнера отменить:

- Связанные отменить функциональность через несколько дизайнеров.

- Детские единицы в дизайнер может взаимодействовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>со своими родителями путем реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и на .

Окружающая среда SDK обеспечивает CodeDOM и настойчивость поддержки путем поставки:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>в качестве реализации<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Предоставлено <xref:System.ComponentModel.Design.IComponentChangeService> Visual Studio дизайн хозяина.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Используйте функции SDK окружающей среды для предоставления отменить поддержку

Чтобы получить отменить поддержку, объект, реализующий конструктор, должен <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> мгновенно и <xref:System.IServiceProvider> инициализировать экземпляр класса с действительной реализацией. Этот <xref:System.IServiceProvider> класс должен предоставить следующие услуги:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Дизайнеры с помощью Visual Studio <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> CodeDOM [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] сериализации может <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>выбрать для использования при условии, что его реализация .

   В этом случае <xref:System.IServiceProvider> класс, <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> предоставленный конструктору, должен вернуть <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> этот объект в качестве реализации класса.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Дизайнеры, <xref:System.ComponentModel.Design.DesignSurface> использующие по умолчанию, предоставляемый visual Studio <xref:System.ComponentModel.Design.IComponentChangeService> design host, гарантированно имеют реализацию класса по умолчанию.

<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Разработчики, реализующие на основе механизма отменить автоматически отслеживает изменения, если:

- Изменения свойств вносятся через <xref:System.ComponentModel.TypeDescriptor> объект.

- <xref:System.ComponentModel.Design.IComponentChangeService>события генерируются вручную при совершении неотоработаемого изменения.

- Модификация на дизайнера была создана в контексте <xref:System.ComponentModel.Design.DesignerTransaction>.

- Дизайнер выбирает явно создавать отменить единиц, используя либо стандартный отменить <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> единицу, предоставляемую <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>реализации или <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> Visual Studio-специфической <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>реализации , которая вытекает из, а также обеспечивает осуществление обоих и .

## <a name="see-also"></a>См. также

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Расширить поддержку проектирования и времени](/previous-versions/37899azc(v=vs.140))
