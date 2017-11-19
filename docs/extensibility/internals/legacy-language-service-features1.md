---
title: "Устаревший языковой службы Features1 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc29529c7ba499cdc7291078774b9f546a3a08ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-features"></a>Возможности службы прежних версий языка
Служба языка framework (MPF) управляемых пакетов может поддерживать один или несколько [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] возможностей, таких как выделение синтаксиса, IntelliSense и проверка точек останова. Каждый компонент может осуществляться независимо от других, но все требуется средство синтаксического анализа и сканер за исключением выделения синтаксиса, что требует только сканер.  
  
## <a name="in-this-section"></a>Содержание  
 [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки языковой пары соответствия, также известные как парные фигурные скобки.  
  
 [Комментирование кода синтаксиса в языковой службе прежних версий](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки комментирования и раскомментировать выделенного кода.  
  
 [Настраиваемые свойства документа в языковой службе прежних версий](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки свойств документа, которые внедряются в исходном файле.  
  
 [Структурирование в языковой службе прежних версий](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки структурирование путем реализации скрытых областей.  
  
 [Переформатирование кода в языковой службе прежних версий](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки форматирования кода.  
  
 [Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки фрагменты кода, которые являются сегментами кода, можно изменить, которые вставляются.  
  
 [Сведения о параметрах в языковую службу прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Описывает, что требуется для поддержки операции сведения о параметре IntelliSense для отображения сигнатуру метода, как типизированный метод.  
  
 [Краткие сведения в языковой службе прежних версий](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки операции краткие сведения IntelliSense для отображения сведений об идентификаторе.  
  
 [Завершение участников в языковой службе прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Описание ресурсов, необходимых для поддержки операции выбора члена пространства имен из списка завершения IntelliSense члена.  
  
 [Завершение машинных слов в языковой службе прежних версий](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Описывает требования для поддержки операции завершения слов IntelliSense для завершения частично типизированного слова.  
  
 [Поддержка окна видимых переменных в языковой службе прежних версий](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Описывает языковую службу можно сделать для поддержки **видимые** окно появляется при отладке.  
  
 [Поддержка панели навигации в языковой службе прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Описывает использование **панель навигации** в верхней части редактора представления для быстрого перехода типов и членов в файле, показанные в этом представлении...  
  
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки выделения синтаксиса исходного кода.  
  
 [Проверка точек останова в языковой службе прежних версий](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Описывает языковую службу можно сделать для поддержки проверки точки останова вне отладчика.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Описывает средство синтаксического анализа и проверки, которые необходимы для реализации всех функций службы языка, которая использует платформы управляемых пакетов.  
  
 [Реализация службы языка для прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Описывает требования для реализации языковую службу с помощью MPF.  
  
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Описывает шаги, необходимые для регистрации службы язык на основе MPF с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Использование технологии IntelliSense](../../ide/using-intellisense.md)  
 Объясняет, как IntelliSense упрощает справочники по языкам, доступ к данным.  
  
 [Реализация службы языка для прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Сведения об использовании платформы управляемых пакетов (MPF) для реализации службы полнофункциональный язык в управляемом коде.