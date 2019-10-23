---
title: Интерфейсы языковой службы прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 065ef972709ca78b516a9acc5f4a737d2963e4b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726847"
---
# <a name="legacy-language-service-interfaces"></a>Интерфейсы языковой службы прежних версий
Для любого конкретного языка программирования в каждый момент времени может существовать только один экземпляр языковой службы. Однако одна языковая служба может обслуживать несколько редакторов.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не связывает языковую службу с каким-либо конкретным редактором. Поэтому при запросе операции языковой службы необходимо выбрать соответствующий редактор в качестве параметра.

## <a name="common-interfaces-associated-with-language-services"></a>Общие интерфейсы, связанные с языковой службой
 Редактор получает языковую службу, вызывая <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> для соответствующего пакета VSPackage. Идентификатор службы (SID), переданный в этом вызове, определяет запрашиваемую языковую службу.

 Интерфейсы основной языковой службы можно реализовать на любом числе отдельных классов. Однако распространенный подход заключается в реализации следующих интерфейсов в одном классе:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (необязательно)

  Интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> должен быть реализован во всех языковых службах. Он предоставляет сведения о языковой службе, такие как локализованное название языка, расширения имен файлов, связанные со службой языка, и способ получения цветового выделения.

## <a name="additional-language-service-interfaces"></a>Дополнительные интерфейсы языковой службы
 Другие интерфейсы могут предоставляться в вашей языковой службе. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запрашивает отдельный экземпляр этих интерфейсов для каждого экземпляра текстового буфера. Поэтому следует реализовать каждый из этих интерфейсов на своем собственном объекте. В следующей таблице показаны интерфейсы, для которых требуется один экземпляр для каждого экземпляра текстового буфера.

|Интерфейс|Описание|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Управляет оформлением окна кода, например раскрывающимся полосой. Этот интерфейс можно получить с помощью метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>. Для каждого окна кода имеется один <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Замечает ключевые слова языка и разделители. Этот интерфейс можно получить с помощью метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> вызывается во время рисования. Избегайте ресурсоемких вычислений в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> или производительности может снизиться.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Предоставляет подсказки параметров IntelliSense. Когда языковая служба распознает символ, указывающий, что следует отображать данные метода, например открытую круглую скобку, он вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>, чтобы уведомить текстовое представление о том, что языковая служба готова отобразить подсказку сведений о параметрах. Затем текстовое представление обращается обратно к языковой службе с помощью методов интерфейса <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>, чтобы получить необходимую информацию для отображения подсказки.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Обеспечивает завершение операторов IntelliSense. Когда языковая служба готова к отображению списка завершения, она вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> в представлении текста. Затем текстовое представление обращается обратно к языковой службе с помощью методов объекта <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Позволяет изменять текстовое представление с помощью обработчика команд. Класс, в котором реализуется интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>, должен также реализовать интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Текстовое представление получает объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>, запрашивая объект <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, который передается в метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>. Для каждого представления должен быть один объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Перехватывает команды, которые пользователь вводит в окно кода. Отслеживание выходных данных в реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> для предоставления настраиваемой информации о завершении и просмотра изменений<br /><br /> Чтобы передать объект <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> в текстовое представление, вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|

## <a name="see-also"></a>См. также
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Контрольный список. Создание языковой службы прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)