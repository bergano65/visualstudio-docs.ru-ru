---
title: Общие сведения о службе языка прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8641a3e009cb5a7b61d8334b6dcb2440d186f4f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131753"
---
# <a name="legacy-language-service-overview"></a>Общие сведения о службе языка прежних версий
Языковая служба поддерживает возможности редактора, позволяет реализовать определенные [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компоненты. Классы Managed Package Framework (MPF) языка службы предоставляют полную поддержку для часто используемых функций и частичная поддержка других возможностей.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Полностью поддерживаемые функции в MPF  
 Классы MPF языковой службы поддерживают следующие функции:  
  
-   Подсветка синтаксиса  
  
-   структуризация  
  
-   Комментирование блоков кода  
  
-   Парные фигурные скобки  
  
-   Фрагменты кода  
  
-   Настраиваемые свойства документа  
  
-   Сведения о параметрах IntelliSense  
  
-   IntelliSense краткие сведения  
  
-   Член завершения IntelliSense  
  
-   Завершение слов IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Частично поддерживаемые функции в MPF  
 MPF только частичный поддерживает следующие функции. Это означает, что необходимо реализовать методы, вызываемые MPF.  
  
-   Переформатирование кода. Вы указываете код, который реализует переформатирование.  
  
-   Проверка точек останова, указав допустимый код диапазонов. Вы указываете код, определяющий фрагментов кода.  
  
-   Поддержка отладчика **видимые** окно для отображения переменных. Можно предоставить код, который определяет, что для отображения в окне.  
  
-   Поддержка **панель навигации** для быстрых переходов между типы и члены. Реализация и возвращают вспомогательный класс, который заполняет списки в **панель навигации** поля со списком.  
  
## <a name="implementation"></a>Реализация  
 Необходимо выполнить ряд действий по реализации языка самой службы и функции службы языка, которые требуется поддерживать для своего языка. Эти действия рассматриваются в следующих разделах:  
  
-   [Реализация службы языка для прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Структурирование в языковой службе прежних версий](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Комментирование кода синтаксиса в языковой службе прежних версий](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Переформатирование кода в языковой службе прежних версий](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Настраиваемые свойства документа в языковой службе прежних версий](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Поддержка панели навигации в языковой службе прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Завершение машинных слов в языковой службе прежних версий](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Завершение участников в языковой службе прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Сведения о параметрах в языковую службу прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Краткие сведения в языковой службе прежних версий](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Поддержка окна видимых переменных в языковой службе прежних версий](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Проверка точек останова в языковой службе прежних версий](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>См. также  
 [Реализация службы языка для прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Расширяемость языковой службы прежних версий](../../extensibility/internals/legacy-language-service-extensibility.md)