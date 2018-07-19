---
title: Строка подключения содержит учетные данные с текстовым паролем и не использует встроенную систему безопасности
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bcd459208529441022669e799e3c59b16b4ef682
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174079"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Строка подключения содержит учетные данные с текстовым паролем и не использует встроенную систему безопасности

Вы хотите сохранить строку подключения к текущему файлу DBML и файлам конфигурации приложения с этой конфиденциальной информацией?  Нажмите кнопку **нет** сохранить строку подключения без конфиденциальной информации.

При работе с подключениями к данным, которые содержат конфиденциальную информацию (пароли, которые включены в строку подключения), предоставляется опция сохранения строки подключения в файл DBML проекта и файл конфигурации приложения с или без конфиденциальной информации.

> [!WARNING]
> Явная установка **подключения** свойства **параметры приложения** свойства **False** добавит пароль в DBML-файл.

## <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Для сохранения строки подключения с конфиденциальной информацией в параметрах приложения проекта

- Нажмите кнопку **Да**.

   Строка подключения сохраняется как параметр приложения. Строка подключения включает конфиденциальную информацию в обычный текст. В файле DBML отсутствует конфиденциальная информация.

## <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Для сохранения строки подключения без конфиденциальной информации в параметрах приложения проекта

- Нажмите кнопку **Нет**.

   Строка подключения сохраняется как параметр приложения, но не включает пароль.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)