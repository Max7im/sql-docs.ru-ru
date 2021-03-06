---
title: Разработка базы данных вне сети с учетом проекта | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.dbprojectwizard.general
- sql.data.tools.dbprojectwizard.summary
ms.assetid: e61e830d-9fcd-45e7-b7b4-93a42155dd56
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6cdd7e27cfba54215f3f2eda52c9132c0b366325
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088016"
---
# <a name="project-oriented-offline-database-development"></a>Разработка базы данных вне сети с учетом проекта
В этом разделе описаны функции SQL Server Data Tools (SSDT) для разработки, создания, отладки и публикации проекта базы данных.  
  
С помощью SSDT вы можете создать проект базы данных вне сети и реализовывать изменения схемы, добавляя, изменяя или удаляя определения объектов (представленные скриптами) в проекте без подключения к экземпляру сервера. Это можно делать с помощью конструктора таблиц или редактора Transact\-SQL. Кроме того, вы можете создавать и отлаживать объекты Transact\-SQL и CLR в одном проекте. Можно с помощью сравнения схем проверять синхронизацию проекта с производственной базой данных, а также создавать моментальные снимки проекта для каждого этапа цикла разработки для сравнения. Работая над проектами баз данных в среде на основе рабочих групп, можно развертывать управление версиями для всех файлов. После разработки, тестирования и отладки проекта можно сдавать его авторизованному персоналу для публикации в рабочей среде.  
  
> [!NOTE]  
> Инструкции этого раздела содержат ряд задач, которые могут выполняться последовательно.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|---------|---------------|  
|[Импорт в проект базы данных](../ssdt/import-into-a-database-project.md)|Описывает импорт объектов из активной базы данных, файла .dacpac или скрипта.|  
|[Диалоговое окно "Добавление ссылки на базу данных"](../ssdt/add-database-reference-dialog-box.md)|Описываются различные способы добавления ссылки на базу данных.|  
|[Диалоговое окно "Проверка наличия обновлений"](../ssdt/check-for-updates-dialog-box.md)|Описывает, как SQL Server Data Tools может проверять наличие обновлений продукта.|  
|[Параметры проекта базы данных](../ssdt/database-project-settings.md)|Описывает различные параметры проекта для управления аспектами базы данных и конфигураций сборки.|  
|[Практическое руководство. Просмотр объектов из проекта базы данных SQL Server](../ssdt/how-to-browse-objects-in-a-sql-server-database-project.md)|В обозревателе объектов SQL Server в Visual Studio теперь добавлен отдельный узел "Проекты", в котором сгруппированы все содержащиеся в решении проекты базы данных SQL Server с использованием иерархии в стиле SQL Server Management Studio.|  
|[Окно операций Data Tools](../ssdt/data-tools-operations-window.md)|Описывает окно **Операции Data Tools** , в котором отображается ход выполнения некоторых операций и выводятся уведомления об ошибках.|  
|[Параметры редактора Transact-SQL](../ssdt/transact-sql-editor-options.md)|Описание параметров Transact\-SQL.|  
|[Практическое руководство. Создание проекта базы данных](../ssdt/how-to-create-a-new-database-project.md)|Создайте проект базы данных и импортируйте существующую схему базы данных.|  
|[Как использовать сравнение схем для сопоставления различных определений баз данных](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)|Сравните схемы базы данных и проекта, выполните синхронизацию.|  
|[Практическое руководство. Сборка и развертывание в локальной базе данных](../ssdt/how-to-build-and-deploy-to-a-local-database.md)|Использование локального экземпляра SQL Server по запросу, который активируется при отладке проекта базы данных.|  
|[Практическое руководство. Изменение целевой платформы и публикация проекта базы данных](../ssdt/how-to-change-target-platform-and-publish-a-database-project.md)|Изменение целевой платформы SQL Server для проекта на любой поддерживаемый экземпляр SQL Server и проверка синтаксиса.|  
|[Практическое руководство. Создание моментального снимка проекта](../ssdt/how-to-create-a-snapshot-of-a-project.md)|Создайте доступный только для чтения прокси схемы базы данных и верните исходный проект, если оказались применены нежелательные изменения.|  
|[Практическое руководство. Использование объектов Microsoft SQL Server 2012 в своем проекте](../ssdt/how-to-use-microsoft-sql-server-2012-objects-in-your-project.md)|Добавьте в проект новый объект последовательности.|  
|[Практическое руководство. Работа с объектами базы данных среды CLR](../ssdt/how-to-work-with-clr-database-objects.md)|Создание и публикация объектов CLR в проекте базы данных SQL Server.|  
|[Практическое руководство. Преобразование проектов базы данных Visual Studio 2010 в проекты базы данных SQL Server с изменением целевой платформы](../ssdt/how-to-convert-visual-studio-2010-database-projects-to-ssql-server-projects.md)|Преобразование существующих баз данных SQL Server, объектов CLR и проектов приложений уровня данных, созданных в Visual Studio 2010, в новый проект Базы данных SQL Server.|  
|[Практическое руководство. Определение скриптов, выполняемых до или после развертывания](../ssdt/how-to-specify-predeployment-or-postdeployment-scripts.md)|Рассматривается порядок использования скриптов, которые выполняются до или после развертывания базы данных.|  
  
## <a name="related-sections"></a>См. также  
[Управление таблицами и связями, а также исправление ошибок](../ssdt/manage-tables-relationships-and-fix-errors.md)  
  
