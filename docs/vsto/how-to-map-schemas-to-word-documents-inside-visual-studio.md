---
title: Как сопоставлять схемы с документами Word в Visual Studio
description: Сведения о сопоставлении схемы XML с Microsoft Officeным документом Word, когда документ открыт в Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 082d5fe4fbcc7f66709770c16d3c9a1a2811e60d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900934"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Как сопоставлять схемы с документами Word в Visual Studio
  **Важно!** Сведения, приведенные в этом разделе о Microsoft Word, предоставляются исключительно для использования в качестве преимуществ и применения частных лиц и организаций, которые находятся за пределами США и его территорий, а также для разработки программ, работающих на платформе Microsoft Word, которые были лицензированы корпорацией Майкрософт до января 2010, когда корпорация Майкрософт удалила реализацию определенных функций, связанных с пользовательским XML-кодом из Microsoft Word Эти сведения, касающиеся Microsoft Word, могут быть не прочитаны или использованы людьми или организациями в США или на ее территориях, которые используют или разрабатывают программные продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г. Эти продукты не будут работать так же, как продукты, лицензированные до этой даты или приобретенные и лицензированные для использования за пределами США.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Схему XML можно сопоставлять с документом, когда документ открыт в Visual Studio. Вы используете те же средства Microsoft Office Word, которые используются, когда документ открыт вне Visual Studio. Проект Office создает те же объекты, когда схема сопоставляется с документом до или после создания решения Word.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Привязка схемы XML к документу Word в Visual Studio

1. Откройте документ Word или шаблон проекта в Visual Studio.

2. Щелкните в документе, чтобы переместить фокус в конструктор.

3. На ленте щелкните вкладку **разработчик** .

    > [!NOTE]
    > Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [инструкции. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. В группе **XML** щелкните **схема**.

     Откроется диалоговое окно **шаблоны и надстройки** .

5. Перейдите на вкладку **XML-схема** .

6. Нажмите кнопку **Добавить схему**.

     Откроется диалоговое окно **Добавление схемы** .

7. Перейдите к файлу схемы, выберите его и нажмите кнопку **Открыть**.

     Откроется диалоговое окно **Параметры схемы** .

8. Назначьте псевдоним или нажмите кнопку " **ОК** ", чтобы добавить схему без псевдонима.

9. Нажмите кнопку **OK**.

     Откроется окно **Структура XML** .

10. Перетащите элементы из окна **Структура XML** в места документа, где нужно создать соответствующие элементы управления.

## <a name="see-also"></a>См. также раздел
- [Как сопоставлять схемы с листами в Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [XML-схемы и данные в настройках уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
