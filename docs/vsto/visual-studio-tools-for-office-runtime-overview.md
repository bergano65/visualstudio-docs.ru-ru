---
title: Visual Studio Tools для среды
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e78d20fa0c7d4d0db6db50c2cbb5cde0b79023fb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086330"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Visual Studio Tools для среды
  Для запуска решений, созданных с помощью средств разработчика Microsoft Office в Visual Studio, Visual Studio 2010 Tools для Office runtime должны устанавливаться на компьютерах конечных пользователей. Дополнительные сведения см. в разделе [Как Установка средств Visual Studio для распространяемого пакета среды выполнения Office](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Visual Studio 2010 Tools для Office runtime состоит из двух основных компонентов:

- Расширения Office для платформы .NET Framework. Эти компоненты представляют собой управляемые сборки, обеспечивающие слой связи между вашим решением и приложением Microsoft Office. Дополнительные сведения см. в разделе [Общие сведения о расширениях Office для .NET Framework](#officeextensions).

- Загрузчик решения Office. Этот компонент представляет собой набор неуправляемых библиотек DLL, которые используются приложениями Office для загрузки среды выполнения и ваших решений. Дополнительные сведения см. в разделе [понять загрузчике решений Office](#UnmanagedLoader).

  Эта среда выполнения может быть установлена несколькими различными способами. В зависимости от конфигурации компьютера при установке среды выполнения устанавливаются различные ее компоненты. Дополнительные сведения см. в разделе [Visual Studio Tools for сценарии установки среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

## <a name="officeextensions"></a> Общие сведения о расширениях Office для .NET Framework
 Visual Studio 2010 Tools для среды выполнения Office содержит расширения Office для платформы .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и более поздних версий. Решения, нацеленные на каждую из версий .NET Framework, используют расширения, соответствующие этой версии.

 Эти расширения состоят из сборок, используемых решениями для автоматизации и расширения приложений Office. При создании проекта Office Visual Studio автоматически добавляет ссылки на сборки, используемые для данного типа проектов и платформы .NET Framework, для которой предназначен этот проект. Дополнительные сведения о сборках в расширениях Office см. в разделе [сборок в Visual Studio Tools для Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

### <a name="design-differences-in-the-office-extensions"></a>Различия разработки в расширениях Office
 Большинство типов, используемых в расширениях Office для .NET Framework 3.5, являются классами. Это те же классы, которые входили в предыдущие версии [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Напротив, большинство типов, которые вы используете в расширениях Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и более поздних версий, являются интерфейсами. Например, при ориентировании на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию типы <xref:Microsoft.Office.Tools.Excel.Worksheet> и <xref:Microsoft.Office.Tools.Word.Document> являются интерфейсами, а не классами.

 В большинстве случаев код, который пишется для решений Office, не зависит от того, для какой платформы он предназначен: .NET Framework 3.5 или [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Однако для некоторых функций требуется различный код, зависящий от версии платформы .NET Framework, для которой он предназначен. Дополнительные сведения см. в разделе [решений Office, перенос на .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Интерфейсы в расширениях Office для .NET Framework 4 или более поздней версии
 Большинство интерфейсов в расширениях Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии не предназначены для реализации с помощью пользовательского кода. Единственными интерфейсами, которые можно реализовать напрямую, имеют имена, начинающиеся с буквы **I**, например <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.

 Все интерфейсы, которые не начинаются с буквы **я** , реализуются внутренним образом средствами Visual Studio 2010 для Office runtime, и эти интерфейсы могут измениться в будущих выпусках. Чтобы создать объекты, реализующие эти интерфейсы, используйте методы, предоставленные объектом `Globals.Factory` в проекте. Например, чтобы получить объект, реализующий интерфейс <xref:Microsoft.Office.Tools.Excel.SmartTag>, используйте метод `Globals.Factory.CreateSmartTag`. Дополнительные сведения о `Globals.Factory`, см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Включение эквивалентности типов и внедренных типов в проектах, предназначенных для .NET Framework 4 или более поздней версии
 Так как объектная модель расширений Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздних версий основана на интерфейсах, можно использовать функцию эквивалентности типов в Visual C# и Visual Basic в Visual Studio для внедрения сведений о типах из [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] в свое решение. Эта функция позволяет раздельно управлять версиями решений Office и [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Например, если в решении используется интерфейс <xref:Microsoft.Office.Tools.Word.Document> в виде внедренного типа и следующая версия среды выполнения добавляет участников в интерфейс <xref:Microsoft.Office.Tools.Word.Document> , решение по-прежнему будет работать со следующей версией среды выполнения. Если в решении не используется интерфейс <xref:Microsoft.Office.Tools.Word.Document> в виде внедренного типа, решение не будет работать в следующей версии среды выполнения.

 По умолчанию функция эквивалентности типов отключена при создании проекта Office, ориентированного на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздние версии. Если ее необходимо включить, задайте свойство **Внедрить типы взаимодействия** любой из следующих ссылок на сборки в проекте как **True**:

- Microsoft.Office.Tools.dll

- Microsoft.Office.Tools.Common.dll

- Microsoft.Office.Tools.Excel.dll

- Microsoft.Office.Tools.Outlook.dll

- Microsoft.Office.Tools.Word.dll

  После внесения этого изменения сведения о типе для всех типов среды выполнения, используемых проектом, внедряются в сборку решения при построении проекта. Эти сведения о внедренных типах, а не сведения о типах в ссылочных сборках, используются решением во время выполнения.

## <a name="UnmanagedLoader"></a> Понять загрузчике решений Office
 Среда выполнения Visual Studio Tools for Office включает несколько неуправляемых библиотек DLL, которые используются приложениями Office для загрузки среды выполнения и решений Office. Хотя работать напрямую с данными библиотеками DLL не следует, необходимо знать их назначение, чтобы лучше понимать архитектуру решений Office.

 Сведения об использовании этих компонентов в процессе загрузки см. в разделе [архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md) и [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="vstoeedll"></a>vstoee.dll
 Когда пользователь открывает настройку уровня документа или запускает надстройку VSTO, приложение Office вызывает библиотеку в *VSTOEE.dll* для выполнения задач, необходимых для загрузки [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

 *Библиотека VSTOEE.dll* гарантирует, что правильная версия [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] загружается для решения и установленной версии Office. Несмотря на то что несколько версий [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] можно установить на одном компьютере, только один экземпляр *VSTOEE.dll* одновременную установку. Это *VSTOEE.dll* , предоставленный последнюю версию среды выполнения, установленную на компьютере. Дополнительные сведения о различных версиях [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , можно использовать для других решений, см. в разделе [запускать решения в различных версиях Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

### <a name="vstoloaderdll"></a>VSTOLoader.dll
 После *VSTOEE.dll* загружает соответствующую версию [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], *VSTOLoader.dll* выполняет большую часть работы, необходимой для загрузки сборки решения. *Библиотека VSTOLoader.dll* выполняет несколько задач:

- Создает домен приложения для каждой сборки решения.

- Выполняет ряд проверок безопасности для подтверждения того, что сборка решения имеет разрешение на выполнение.

- Загружает версию расширений Office для платформы .NET Framework, которая требуется для этого решения.

  *Библиотека VSTOLoader.dll* также выполняет ряд задач, характерные для надстроек VSTO:

- Реализует интерфейс <xref:Extensibility.IDTExtensibility2> . Интерфейс<xref:Extensibility.IDTExtensibility2> — это COM-интерфейс, который должен реализовываться всеми надстройками VSTO для приложений Microsoft Office. С помощью этого интерфейса определяются методы, вызываемые приложением для взаимодействия с надстройкой VSTO.

- Он реализует интерфейс IManagedAddin. Этот интерфейс используется приложениями Office, помогая загружать надстройки VSTO. Дополнительные сведения см. в разделе [интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md).

## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Понять 32-разрядных и 64-разрядных версиях среды выполнения
 Существуют отдельные 64-разрядных и 32-разрядные версии средств Visual Studio 2010 для Office runtime. Эти версии среды выполнения используются для запуска решений в 64- и 32-разрядных выпусках Office. В следующей таблице показано, какие версии среды выполнения необходимы для каждого сочетания Windows и Office.

|Выпуск Windows|Выпуск Microsoft Office|Необходимая версия среды выполнения Visual Studio Tools for Office|
|------------------------|---------------------------------|--------------------------------------------------------------------|
|32-разрядная версия|32-разрядная версия|32-разрядная версия|
|64-разрядная версия|32-разрядная версия|64-разрядная версия|
|64-разрядная версия|64-разрядная версия|64-разрядная версия|

 При установке Office необходимая версия [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] устанавливается вместе с Office. Например, при установке 64-разрядного выпуска Office в 64-разрядную версию Windows также устанавливается 64-разрядная версия [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Дополнительные сведения об установке [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] с Office, см. в разделе [Visual Studio Tools for сценарии установки среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

 Решения Office, созданные с использованием шаблонов проектов для выпуска 2007 системы Microsoft Office в Visual Studio 2008, также работают в 64-разрядной версии Office. Однако решения Office, созданные с использованием шаблонов проектов для Microsoft Office 2003 в Visual Studio 2008 или Visual Studio 2005, в этой версии не работают. Дополнительные сведения см. в разделе [запускать решения в различных версиях Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Восстановление Visual Studio 2010 Tools для Office runtime
 При необходимости устранить ошибки в среде выполнения откройте окно **Программы и компоненты** или **Установка и удаление программ** на панели управления, выберите в списке программ **Среда выполнения средств Microsoft Visual Studio 2010 для Office** и нажмите кнопку **Удалить**. Запущенная программа установки позволяет удалить ошибки среды выполнения. При выборе команды **Изменить**пользователь не получает возможности удалить ошибки среды выполнения.

## <a name="see-also"></a>См. также
- [Visual Studio Tools для сценарии установки среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Сборки в Visual Studio Tools для Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
- [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)
- [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Обновление и перенос решений Office](../vsto/upgrading-and-migrating-office-solutions.md)
