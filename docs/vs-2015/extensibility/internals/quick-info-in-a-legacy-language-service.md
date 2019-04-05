---
title: Краткие сведения в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f27b58b4ef94f4b859b43c2321ddbd9b67327fe
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993632"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Краткие сведения в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Краткие сведения IntelliSense отображаются сведения об идентификаторе в источнике, когда пользователь помещает курсор в идентификаторе и выбирает **краткие сведения** из **IntelliSense** меню или удерживает указатель мыши курсор над ним. В этом случае отображаются с информацией о идентификатор всплывающей подсказки. Эти сведения обычно состоит из идентификатора типа. Когда отладчик активен, эта информация может включать текущее значение. Модуль отладки предоставляет значения выражения, хотя языковая служба обрабатывает только идентификаторы.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [Пошаговое руководство: Отображение всплывающих подсказок для кратких сведений](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
 Управляемых пакетов framework (MPF) языка службы классы обеспечивают полную поддержку для отображения всплывающей подсказки краткие сведения IntelliSense. Что необходимо сделать всего лишь предоставить текст для отображения и включение функции краткие сведения.  
  
 Текст, отображаемый получается путем вызова <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> средство синтаксического анализа метод со значением причина синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. Поэтому сообщает средство синтаксического анализа, чтобы получить сведения о типе (или соответствующие действия для отображения в подсказке) для идентификатора в расположении, указанном в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта. <xref:Microsoft.VisualStudio.Package.ParseRequest> Является объект, которые были переданы <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод.  
  
 Средство синтаксического анализа должно проанализировать все, что до позиции в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта, чтобы определить, какие все идентификаторы. Затем средство синтаксического анализа необходимо получить идентификатор в расположении синтаксического анализа запроса. Наконец, средство синтаксического анализа необходимо передать данные tip средства, связанные с этого идентификатора к <xref:Microsoft.VisualStudio.Package.AuthoringScope> таким образом, этот объект может возвращать текст из <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> метод.  
  
## <a name="enabling-the-quick-info-feature"></a>Включение функции краткие сведения  
 Чтобы включить функцию краткие сведения, необходимо задать `CodeSense` и `QuickInfo` именованные параметры из <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Задайте эти атрибуты <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> и <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> свойства.  
  
## <a name="implementing-the-quick-info-feature"></a>Реализация функции краткие сведения  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> Класс обрабатывает операции краткие сведения IntelliSense. При <xref:Microsoft.VisualStudio.Package.ViewFilter> класс получает <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команды, класс вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод с причиной по синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> и расположение курсора во время <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команда была отправлена. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Метод синтаксического анализа необходимо затем проанализировать источника до заданного расположения и последующего синтаксического анализа идентификатора в указанном расположении, чтобы определить, что для отображения в подсказке.  
  
 Большинство средств синтаксического анализа сделать начального анализа всего исходного файла и сохранение результатов в дерево синтаксического анализа. Полный анализ выполняется при <xref:Microsoft.VisualStudio.Package.ParseReason> передается <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод. Другие виды синтаксического анализа можно использовать для получения требуемой информации дерево синтаксического анализа.  
  
 Например, синтаксический анализ причин значение <xref:Microsoft.VisualStudio.Package.ParseReason> можно найти идентификатор в исходном расположении и найти в дереве синтаксического анализа, чтобы получить сведения о типе. Эти сведения о типах затем передается <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса и возвращается функциями <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> метод.
