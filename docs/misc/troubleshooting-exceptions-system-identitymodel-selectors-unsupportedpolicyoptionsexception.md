---
title: "Разрешение вопросов, связанных с исключениями: System.IdentityModel.Selectors.UnsupportedPolicyOptionsException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.IdentityModel.Selectors.UnsupportedPolicyOptionsException - исключение"
  - "UnsupportedPolicyOptionsException - исключение"
ms.assetid: 1151127d-81a1-4d87-8462-924ab9d1ee01
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.IdentityModel.Selectors.UnsupportedPolicyOptionsException
Исключение <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException> указывает, что политика, предоставленная системе, содержит параметры, которые не поддерживаются. Следующие ограничения могут вызвать эти ошибки.  
  
 Адресат запросил маркер у службы маркеров локальной безопасности, указав "http:\/\/schemas.xmlsoap.org\/ws\/2005\/05\/Identity\/issuer\/self" в качестве поставщика маркера. Однако, одно из требований, описанных в политике, не поддерживается службой маркеров локальной безопасности CardSpace. Дополнительные сведения см. в разделе [Технический справочник по Information Card Profile V1.0](http://go.microsoft.com/fwlink/?LinkId=102401). Примеры неподдерживаемых параметров:  
  
-   Требование получателя отсутствует в списке поддерживаемых требований, указанном в разделе [Поддерживаемые типы требований](http://go.microsoft.com/fwlink/?LinkId=102402) "Технического справочника по Information Card Profile V1.0".  
  
-   тип маркера отличен от SAML 1.0 или 1.1;  
  
-   для не\-SSL узелов: используется ключ, отличный от симметричного ключа;  
  
-   KeyWrapAlgorithm отличается от алгоритма по умолчанию;  
  
-   в политике указан неподдерживаемый элемент. Поддерживаемые элементы:  
  
    -   EncryptionAlgorithm  
  
    -   CanonicalizationAlgorithm  
  
    -   SignWith  
  
    -   TokenType  
  
    -   ClaimsElement  
  
    -   KeyType  
  
    -   KeySize  
  
    -   EncryptWith  
  
    -   RequestType  
  
    -   SecondaryParameters  
  
    -   KeyWrapAlgorithm  
  
-   WST:RequestType имеет тип, отличный от Issue;  
  
-   для асимметричных типов ключа, размер ключа не равен 2048.  
  
## См. также  
 <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)