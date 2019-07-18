---
title: Общие сведения о службе прежней версией языка | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5964aa82d76791d29313ac787f1216c9c9ad283
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202716"
---
# <a name="legacy-language-service-overview"></a>Обзор языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Служба языка предоставляет поддержку редактора, которая позволяет реализовывать определенные [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] функции. Классы Managed Package Framework (MPF) языка службы обеспечивают полную поддержку для часто используемых функций и частичная поддержка других функций.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Полностью поддерживаемые функции в MPF  
 Классы MPF языковой службы поддерживают следующие функции:  
  
- Подсветка синтаксиса  
  
- Структуризация  
  
- Комментирование блоков кода  
  
- Парные фигурные скобки  
  
- Фрагменты кода  
  
- Настраиваемые свойства документа  
  
- Сведения о параметрах IntelliSense  
  
- IntelliSense краткие сведения  
  
- Автозавершение элементов IntelliSense  
  
- Завершение слов IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Частично поддерживаемые функции в MPF  
 MPF только частичный поддерживает следующие функции. Это означает, что необходимо реализовать методы, вызываемые MPF.  
  
- Переформатирование кода. Вы указываете код, реализующий переформатирование.  
  
- Проверка точек останова, указав допустимый код диапазонов. Вы указываете код, определяющий диапазоны кода.  
  
- Поддержка отладчика **"Видимые"** окно для отображения переменных. Можно предоставить код, который определяет, что для отображения в окне.  
  
- Поддержка **панель навигации** для быстрого перехода между типы и члены. Вы реализуете и возвращать вспомогательный класс, который заполняет списки в **панель навигации** поля со списком.  
  
## <a name="implementation"></a>Реализация  
 Необходимо выполнить ряд действий по реализации самой службы языка и функциям службы языка, которые требуется поддерживать для своего языка. Эти действия рассматриваются в следующих разделах:  
  
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
- [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
- [Структурирование в языковой службе прежних версий](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
- [Комментирование кода синтаксиса в языковой службе прежних версий](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
- [Переформатирование кода в языковой службе прежних версий](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
- [Настраиваемые свойства документа в языковой службе прежних версий](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
- [Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
- [Поддержка панели навигации в языковой службе прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
- [Завершение машинных слов в языковой службе прежних версий](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
- [Завершение участников в языковой службе прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
- [Сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
- [Краткие сведения в языковой службе прежних версий](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
- [Поддержка окна видимых переменных в языковой службе прежних версий](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
- [Проверка точек останова в языковой службе прежних версий](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>См. также  
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Расширяемость языковой службы прежних версий](../../extensibility/internals/legacy-language-service-extensibility.md)
