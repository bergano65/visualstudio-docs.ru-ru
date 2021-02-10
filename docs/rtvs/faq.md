---
title: Часто задаваемые вопросы об инструментах R в Visual Studio
description: Часто задаваемые вопросы об R в Visual Studio.
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: ecb64f12783b99cd0f26c59ee4ee298c5fabde72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885759"
---
# <a name="frequently-asked-questions"></a>Часто задаваемые вопросы

## <a name="visual-studio-support"></a>Поддержка Visual Studio

**В. Работает ли RTVS на OS X или Linux?**

A. Инструменты RTVS в настоящее время строятся только на основе среды Visual Studio, которая реализована только для Windows. Корпорация Майкрософт изучает возможность поддержки Visual Studio Code и Visual Studio для Mac. См. описание [проблемы RTVS № 1295](https://github.com/Microsoft/RTVS/issues/1295).

**В. Работает ли RTVS с выпусками Visual Studio Express?**

A. Нет.

**В. Можно ли использовать расширения Visual Studio с RTVS?**

A. Конечно. Вот некоторые расширения, которые пользуются популярностью у пользователей, работающих с R.

- [VsVim для настраиваемых сочетаний клавиш Vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Редактор Markdown с интерактивным предварительным просмотром](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Дополнительные сведения см. в магазине [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

**В. Если RTVS работает в Visual Studio, означает ли это, что R можно легко использовать с C#, C++ и другими языками Майкрософт?**

A. Нет. RTVS — это средство для разработки кода R, которое использует собственные стандартные интерпретаторы R. Взаимодействие R с другими языками сейчас не поддерживается.

**В. Есть ли версия RTVS не на английском языке?**

A. Выпуск RTVS 1.0 доступен только на английском языке. Выпуск 1.1 будет локализован на те же языки, что и сама среда Visual Studio. Пока вы можете использовать [пакет английского языка для Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157). Или в Visual Studio 2017 запустите программу установки и выберите английский язык на вкладке **Языковые пакеты**.

![Региональные параметры для Visual Studio 2017.](media/FAQ-international-settings.png)

**В. Мне очень нравятся мои текущие параметры Visual Studio, но я хочу попробовать новые параметры обработки и анализа данных. Что нужно сделать?**

A. Сохраните текущие параметры Visual Studio с помощью команды **Сервис** > **Импорт и экспорт параметров**, затем перейдите к параметрам обработки и анализа данных. Чтобы восстановить сохраненные параметры, еще раз используйте команду **Импорт и экспорт параметров**.

**В. Можно ли хранить проект Visual Studio в общей сетевой папке?**

A. Нет, Visual Studio не поддерживает загрузку проектов из общей сетевой папки.

## <a name="r-interpretersintegration"></a>Интерпретаторы и интеграция R

**В. С какими интерпретаторами R работает RTVS?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R Client и Microsoft Machine Learning Server](/machine-learning-server/)

**В. Где можно скачать интерпретаторы?**

A. На странице [установки](installing-r-tools-for-visual-studio.md).

В. **Что такое Microsoft R Server?**

A. R Server — это прежнее название [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**В. Работает ли RTVS с 32-разрядными версиями R?**

A. Нет, RTVS поддерживает только 64-разрядные выпуски R, работающие в 64-разрядных выпусках Windows.

**В. Работает ли RTVS с моей системой управления версиями?**

A. Да, вы можете использовать любую систему управления версиями, которая интегрирована в Visual Studio.

**В. Какие параметры *GITIGNORE* рекомендуются для проекта RTVS?**

A. GitHub поддерживает репозиторий рекомендуемых файлов *GITIGNORE*. Он находится здесь: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Удаленные службы

У. **Что такое удаленные службы в Visual Studio?**

A. Удаленные службы R для Visual Studio позволяют настроить компьютер Windows или Linux, чтобы затем подключаться к нему из RTVS. См. раздел [Настройка удаленных рабочих областей](setting-up-remote-r-workspaces.md).

У. **Может ли RTVS подключиться к Microsoft Machine Learning Server?**

A. Нет, так как Microsoft ML Server — это другая технология, механизм подключения которой не отвечает требованиям RTVS.

У. **Могут ли Инструменты R для Visual Studio подключаться к виртуальной машине, созданной с помощью образа виртуальной машины для обработки и анализа данных в Azure?**

A. Да. Образ [виртуальной машины для обработки и анализа данных для Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) предварительно устанавливается с удаленными службами R для Visual Studio.

В. **Могут ли Инструменты R для Visual Studio подключаться к удаленному компьютеру с установленной средой R?**

Для выполнения кода на языке R на удаленном компьютере требуется служба, ожидающая запросы, принимающая код и отправляющая результаты обратно на клиентский компьютер. Именно этим занимаются удаленные службы R для Visual Studio. См. раздел [Настройка удаленных рабочих областей](setting-up-remote-r-workspaces.md).

У. **Что такое удаленный сеанс?**

A. См. статью [Выполнение на удаленном сервере](/machine-learning-server/r/how-to-execute-code-remotely) в документации по Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Разработка и возможности Инструментов R для Visual Studio

**В. Отсутствует компонент X, но он есть в RStudio.**

A. RStudio — прекрасная продуманная среда IDE для R, разрабатываемая в течение многих лет. Мы стараемся обеспечить RTVS всеми компонентами, которые необходимы вам для успешной работы. Помогите нам определить приоритет будущих действий, сообщив о проблеме через [GitHub](https://github.com/Microsoft/RTVS/issues/).

**В. Можно ли участвовать в разработке RTVS?**

A. Конечно. Исходный код находится на [GitHub](https://github.com/microsoft/RTVS). Отправляйте найденные ошибки и свои комментарии в систему отслеживания проблем.

Вы также можете внести вклад в создание этой документации: &mdash;просто выберите команду **Изменить** в правом верхнем углу любой страницы. Комментарии к документации тоже приветствуются. Вы можете добавлять их в нижней части любой страницы.
