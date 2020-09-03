---
title: Устаревшая языковая служба Features1 | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196128"
---
# <a name="legacy-language-service-features"></a>Функции языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Языковая служба управляемого пакета (MPF) может поддерживать одну или несколько [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] функций, таких как выделение синтаксиса, IntelliSense и проверка точки останова. Каждая функция может быть реализована независимо от других, но для всех требуется средство синтаксического анализа и сканер, за исключением выделения синтаксиса, для которого требуется только сканер.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки сопоставления пар языков, также известных как Парные фигурные скобки.  
  
 [Комментирование кода синтаксиса в языковой службе прежних версий](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки комментирования и комментирования выбранного кода.  
  
 [Настраиваемые свойства документа в языковой службе прежних версий](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки свойств документа, внедренных в исходный файл.  
  
 [Структурирование в языковой службе прежних версий](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки структурирования посредством реализации скрытых регионов.  
  
 [Переформатирование кода в языковой службе прежних версий](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки переформатирования кода.  
  
 [Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки фрагментов кода, которые являются частями кода, которые вставляются и могут быть изменены.  
  
 [Сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Описывает, что требуется для поддержки операции со сведениями о параметрах IntelliSense для отображения сигнатуры метода при вводе метода.  
  
 [Краткие сведения в языковой службе прежних версий](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки операции быстрой информации IntelliSense для отображения сведений об идентификаторе.  
  
 [Завершение участников в языковой службе прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки операции завершения элементов IntelliSense для выбора члена пространства имен из списка.  
  
 [Завершение машинных слов в языковой службе прежних версий](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки операции слова Complete в IntelliSense для завершения частично типизированных слов.  
  
 [Поддержка окна видимых переменных в языковой службе прежних версий](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Описывает, что может сделать языковая служба для поддержки окна " **видимые** " во время отладки.  
  
 [Поддержка панели навигации в языковой службе прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Описывает, как использовать **панель навигации** в верхней части представления редактора для быстрого перехода к любому типу или члену в файле, показанном в этом представлении.  
  
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки выделения синтаксиса исходного кода.  
  
 [Проверка точек останова в языковой службе прежних версий](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Описывает, что может сделать языковая служба для поддержки проверки точек останова за пределами отладчика.  
  
## <a name="related-sections"></a>См. также  
 [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Описывает средство синтаксического анализа и сканер, необходимые для реализации всех функций языковой службы, использующей платформу управляемых пакетов.  
  
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Описывает, что необходимо для реализации языковой службы с помощью MPF.  
  
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Описание действий, необходимых для регистрации службы языка на основе MPF с помощью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Использование технологии IntelliSense](../../ide/using-intellisense.md)  
 Объясняет, как IntelliSense упрощает доступ к языковой ссылке.  
  
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Содержит сведения об использовании платформы управляемых пакетов (MPF) для реализации полнофункциональной языковой службы в управляемом коде.
