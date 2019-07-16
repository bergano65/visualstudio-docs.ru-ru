---
title: Устаревший языковой службы Features1 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9506c6756c785741c40f86ae5839101bf0079854
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196128"
---
# <a name="legacy-language-service-features"></a>Функции службы устаревшего языка
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Службы языка framework (MPF) управляемых пакетов может поддерживать один или несколько [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] функции, такие как выделение синтаксических конструкций, IntelliSense и проверка точек останова. Каждый компонент может быть реализован независимо от других, но все требуют средство синтаксического анализа и сканер за исключением выделения синтаксиса, который требует только сканера.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Описываются новые возможности, необходимые для поддержки языковой пары, сопоставления, также известный как парные фигурные скобки.  
  
 [Комментирование кода синтаксиса в языковой службе прежних версий](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Описываются новые возможности, необходимые для поддержки добавления и удаления комментариев выделенного кода.  
  
 [Настраиваемые свойства документа в языковой службе прежних версий](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Описываются новые возможности, необходимые для поддержки свойств документа, которые внедряются в исходном файле.  
  
 [Структурирование в языковой службе прежних версий](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Описывает, как поддержка структурирования путем реализации скрытых областей.  
  
 [Переформатирование кода в языковой службе прежних версий](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Описываются новые возможности, необходимые для поддержки переформатирования кода.  
  
 [Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Описываются новые возможности, необходимые для поддержки фрагменты кода, представляющих собой сегменты кода, которые вставляются и могут редактироваться.  
  
 [Сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Описываются новые возможности, необходимые для поддержки операции IntelliSense сведения о параметрах для отображения подписи метода, как метод введено.  
  
 [Краткие сведения в языковой службе прежних версий](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Описываются новые возможности, необходимые для поддержки операции краткие сведения IntelliSense для отображения сведений об идентификаторе.  
  
 [Завершение участников в языковой службе прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки операции IntelliSense автозавершение элементов для выбора члена пространства имен из списка.  
  
 [Завершение машинных слов в языковой службе прежних версий](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Описываются новые возможности, необходимые для поддержки операции автоматического завершения слов IntelliSense для завершения частично вводимых слов.  
  
 [Поддержка окна видимых переменных в языковой службе прежних версий](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Описывает возможности языковой службы для поддержки **"Видимые"** окно при отладке.  
  
 [Поддержка панели навигации в языковой службе прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Описывает использование **панель навигации** в верхней части редактора представления для быстрого перехода любого типа или члена в файл, показанный в этом представлении...  
  
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Описываются новые возможности, необходимые для поддержки подсветки синтаксиса исходного кода.  
  
 [Проверка точек останова в языковой службе прежних версий](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Описывает возможности языковой службы для поддержки проверки точки останова вне отладчика.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Описывает средство синтаксического анализа и сканер, который должны реализовать все возможности языковой службы, которая использует managed package framework.  
  
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Описывает, что он должен реализовывать языковую службу с помощью MPF.  
  
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Описание действий, которые необходимо зарегистрировать службу языка на основе MPF с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Использование технологии IntelliSense](../../ide/using-intellisense.md)  
 Объясняет, как IntelliSense позволяет справочники по языкам, можно легко получить доступ.  
  
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Сведения об использовании managed package framework (MPF) для реализации полнофункционального языковой службы в управляемом коде.
