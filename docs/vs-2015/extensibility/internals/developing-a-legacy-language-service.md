---
title: Разработка языковой службы прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 36ff8335bfaf99b5826d217a48910bfd581321e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842765"
---
# <a name="developing-a-legacy-language-service"></a>Разработка языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В этом разделе содержатся ссылки на разделы, которые помогут создать устаревшую языковую службу.  
  
 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации языковой службы см. в статье [расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Модель языковой службы прежних версий](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Предоставляет модель службы минимального языка для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] базового редактора. Эту модель можно использовать в качестве руководств по созданию собственной языковой службы.  
  
 [Интерфейсы языковой службы прежних версий](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Описывает объекты, необходимые для реализации языковой службы, и предоставляет список дополнительных объектов, которые можно использовать для выделения синтаксических конструкций, данных методов и других функций.  
  
 [Перехват команд языковой службы прежних версий](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Описание вставки фильтра команд в языковую службу для перехвата команд, которые в противном случае будут обработаны в текстовом представлении.  
  
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Содержит сведения о регистрации языковой службы с помощью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Поддержка языковой службы для отладки](../../extensibility/internals/language-service-support-for-debugging.md)  
 Описывает, как языковая служба может предоставлять функции для поддержки отладчика.  
  
 [Контрольный список. Создание языковой службы прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Содержит пошаговые инструкции по созданию и интеграции языковой службы для базового редактора.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Описывает, как реализовать выделение синтаксиса в языковой службе.  
  
 [Завершение операторов в языковой службе прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Обсуждается завершение операторов, процесс, с помощью которого служба языка помогает пользователям завершить ключевое слово языка или элемент, который они начали вводить.  
  
 [Сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Описывает способы предоставления советов по методам для перегруженных функций и методов.  
  
 [Практическое руководство. Поддержка скрытого текста в языковой службе прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Объясняет назначение скрытой области текста и предоставляет инструкции о том, как реализовать скрытую область текста.  
  
 [Практическое руководство. Расширенная поддержка структурирования в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Описание двух вариантов, расширяющих поддержку структурирования для вашего языка, после того как команда *Свернуть в определения* не поддерживается.
