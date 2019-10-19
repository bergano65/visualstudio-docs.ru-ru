---
title: Интеграция с редактором XML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c0d1088e9932613466209ef8517ac5035c0b613
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656255"
---
# <a name="integration-with-xml-editor"></a>Интеграция с редактором XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Конструктор XML-схем объединен с редактором XML. При изменении XSD-файла в редакторе XML это изменение будет отражено в [обозревателе XML-схем](../xml-tools/xml-schema-explorer.md). Если открыто представление [графика](../xml-tools/graph-view.md) или [модель содержимого](../xml-tools/content-model-view.md) , то это изменение также будет отражено там. Можно перемещаться между конструктором XML-схем и редактором XML, используя любой из следующих методов.

- В редакторе XML щелкните правой кнопкой мыши узел и выберите команду **отобразить в обозревателе XML-схемы**.

- В представлении графика и обозревателе XML-схем дважды щелкните узел или щелкните узел правой кнопкой мыши и выберите команду **Просмотреть код**. В представлении модель содержимого щелкните правой кнопкой мыши узел и выберите команду **Просмотреть код**.

  На следующем снимке экрана показана схема XML, открытая в обозревателе XML-схем. Обозреватель XML-схем отображает набор схем в виде дерева. XML Editor отображает текстовый вид узла, который сейчас активен в обозревателе XML-схем.

  ![кссддесигнервисксмледитор](../xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")

  В некоторых случаях рекомендуется просматривать код в редакторе XML и графическом конструкторе параллельно. Чтобы одновременно просмотреть оба файла, щелкните правой кнопкой мыши в любом месте редактора XML и выберите пункт **Конструктор представлений**. В меню окна Visual Studio выберите пункт **Новая горизонтальная (или вертикальная) группа вкладок**.

  ![кссддесигнервисксмледиторандкмв](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")

## <a name="see-also"></a>См. также раздел
 [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)
