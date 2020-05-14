---
title: Устаревшие интерфейсы языковых служб (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707385"
---
# <a name="legacy-language-service-interfaces"></a>Интерфейсы языковой службы прежних версий
Для любого конкретного языка программирования может быть только один экземпляр языковой службы одновременно. Тем не менее, один языковой сервис может обслуживать более одного редактора.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]не связывает языковую службу с каким-либо конкретным редактором. Поэтому при запросе операции языковой службы необходимо определить соответствующий редактор в качестве параметра.

## <a name="common-interfaces-associated-with-language-services"></a>Общие интерфейсы, связанные с языковыми службами
 Редактор получает вашу языковую <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> услугу, позвонив по соответствующему VSPackage. Идентификатор службы (SID), передаваемый в этом вызове, определяет запрашиваемую языковую службу.

 Интерфейсы основных языковых служб можно реализовать в любом количестве отдельных классов. Однако общий подход заключается в реализации следующих интерфейсов в одном классе:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- Среда <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (необязательно)

  Интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> должен быть реализован на всех языковых службах. В нем содержится информация о вашей языковой службе, например, локализованное имя языка, расширение имен файлов, связанных с языковой службой, и способ получения цветоизолятора.

## <a name="additional-language-service-interfaces"></a>Дополнительные интерфейсы языковых служб
 Другие интерфейсы могут быть предоставлены с вашим языковым сервисом. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]запрашивает отдельный экземпляр этих интерфейсов для каждого экземпляра буфера текста. Поэтому необходимо реализовать каждый из этих интерфейсов на своем объекте. В следующей таблице показаны интерфейсы, требующие одного экземпляра на экземпляр буфера текста.

|Интерфейс|Описание|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Управляет украшениями окна кода, такими как выпадающий бар. Вы можете получить этот <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> интерфейс с помощью метода. Существует один <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> на код окна.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Раскрашивает ключевые слова языка и разграничивые. Вы можете получить этот <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> интерфейс с помощью метода. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>называется во время краски. Избегайте вычислительной интенсивной работы внутри <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> или производительность может пострадать.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Предоставляет параметры инструментов IntelliSense. Когда языковая служба распознает символ, указывающий на то, что данные метода должны <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> отображаться, например, открытый скобки, он называет метод, чтобы уведомить текстовое представление о том, что языковая служба готова отображать Параметр Info ToolTip. Текстовое представление затем перезванивает в языковую службу, используя методы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейса для получения необходимой информации для отображения инструментария.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Обеспечивает завершение оператора IntelliSense. Когда языковая служба готова отображать список завершения, она вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод в текстовом представлении. Текстовое представление затем перезванивает в языковую <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> службу с помощью методов на объекте.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Позволяет изменить текстовое представление с помощью обработчика команд. Класс, в котором <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> вы реализуете <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, также должен реализовать интерфейс. Текстовое представление извлекает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> объект, задав запрос <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объекту, который передается в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод. Для каждого <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> представления должен быть один объект.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Перехватов овешнок, который пользователь вводит в окне кода. Мониторинг вывода <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> из реализации для предоставления пользовательской информации о завершении и изменения представления<br /><br /> Чтобы передать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объект текстовому <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>представлению, позвоните .|

## <a name="see-also"></a>См. также
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Контрольный список. Создание языковой службы прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
