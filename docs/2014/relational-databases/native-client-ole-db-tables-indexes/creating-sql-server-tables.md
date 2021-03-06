---
title: Создание таблиц SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- SQL Server Native Client OLE DB provider, tables
- DBCOLUMNDESC usage
- adding tables
- CreateTable function
ms.assetid: a7b8d142-d76a-44d9-a583-86ac5109fbe8
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a0c56c25e5904a65fdbf24e4b3bcf7a2c98d9c7a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429393"
---
# <a name="creating-sql-server-tables"></a>Создание таблиц SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **ITableDefinition::CreateTable** функция, которая позволяет потребителям создавать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблиц. Потребители используют **CreateTable** для создания именованных потребителем постоянных таблиц, а также постоянных и временных таблиц с уникальными именами, созданными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.  
  
 Когда потребитель вызывает **ITableDefinition::CreateTable**, если значение свойства DBPROP_TBL_TEMPTABLE имеет значение VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента создает имя временной таблицы для потребителя. Потребитель устанавливает *pTableID* параметр **CreateTable** значение NULL. Временные таблицы с именами, сформированными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента не отображаются в **ТАБЛИЦ** набора строк, но можно получить при помощи **IOpenRowset** интерфейс.  
  
 Когда потребители задают имя таблицы в *pwszName* членом *uName* объединения в *pTableID* параметра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента Создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы с таким именем. Имя таблицы подчиняется ограничениям для имен таблиц, принятым в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и может указывать на постоянную таблицу, а также локальную или глобальную временную таблицу. Дополнительные сведения см. в разделе [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql). *PpTableID* параметр может иметь значение NULL.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента можно формировать имена постоянных и временных таблиц. Когда потребитель устанавливает *pTableID* параметр значение NULL и наборы *ppTableID* указывал на допустимый DBID\*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента возвращает создаваемое имя в таблицу *pwszName* членом *uName* объединение DBID, на которые указывают значение *ppTableID*. Чтобы создать временный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу с именем поставщика OLE DB для собственного клиента, потребитель включает свойство таблицы OLE DB DBPROP_TBL_TEMPTABLE в набор, на которые имеются ссылки в свойств таблицы *rgPropertySets* параметра. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Собственный клиент OLE DB с именем поставщика временные таблицы являются локальными.  
  
 **CreateTable** возвращает значение DB_E_BADTABLEID, если *eKind* членом *pTableID* не указывает на DBKIND_NAME.  
  
## <a name="dbcolumndesc-usage"></a>Использование структуры DBCOLUMNDESC  
 Потребитель может задать тип данных столбца, либо при помощи *pwszTypeName* члена или *wType* член. Если потребитель указывает тип данных в *pwszTypeName*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента не учитывает значение *wType*.  
  
 При использовании *pwszTypeName* , потребитель задает тип данных с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имена типов данных. Допустимыми являются имена типов данных, возвращаемые в столбце TYPE_NAME набора строк схемы PROVIDER_TYPES.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента распознает подмножество значений DBTYPE перечисления OLE DB *wType* член. Дополнительные сведения см. в разделе [сопоставления типов данных в интерфейсе ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).  
  
> [!NOTE]  
>  **CreateTable** возвращает значение DB_E_BADTYPE, если потребитель *pTypeInfo* или *pclsid* указал тип данных столбца.  
  
 Потребитель указывает имя столбца в *pwszName* членом *uName* объединения структуры DBCOLUMNDESC *dbcid* член. Имя столбца задается в виде символьной строки в Юникоде. *EKind* членом *dbcid* должен быть равен DBKIND_NAME. **CreateTable** возвращает значение DB_E_BADCOLUMNID, если *eKind* является недопустимым, *pwszName* имеет значение NULL, или, если значение *pwszName* не является допустимым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификатор.  
  
 Все свойства столбцов доступны для всех столбцов, определенных в данной таблице. **CreateTable** может вернуть DB_S_ERRORSOCCURRED или DB_E_ERRORSOCCURRED, если заданы значения свойства, участвующего в конфликте. **CreateTable** возвращает ошибку, если недопустимые значения свойств столбцов вызывают [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сбой при создании таблицы.  
  
 Свойства столбцов в структуре DBCOLUMNDESC интерпретируются следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|И запись: чтение и запись<br /><br /> Значение по умолчанию — Значение VARIANT_FALSE Описание: задает свойство идентификатора для создаваемого столбца. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство идентификатора может иметь только один столбец таблицы. Свойству присвоено значение VARIANT_TRUE для нескольких столбцов, возникнет ошибка при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается создать таблицу на сервере.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Свойство identity допустимо только для **целое число**, **числовых**, и **десятичное** типов, когда масштаб равен 0. Свойству присвоено значение VARIANT_TRUE для столбца любого другого типа данных приводит к ошибке при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается создать таблицу на сервере.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение DB_S_ERRORSOCCURRED, если свойства DBPROP_COL_AUTOINCREMENT и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE и *dwOption* свойства DBPROP_COL_NULLABLE не DBPROPOPTIONS_ Обязательно. Если DBPROP_COL_AUTOINCREMENT и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE, то возвращается ошибка DB_E_ERRORSOCCURRED и *dwOption* свойства DBPROP_COL_NULLABLE равен DBPROPOPTIONS_REQUIRED. Столбец определяется с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство identity и DBPROP_COL_NULLABLE *dwStatus* устанавливается значение DBPROPSTATUS_CONFLICTING.|  
|DBPROP_COL_DEFAULT|И запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ограничение по умолчанию для столбца.<br /><br /> *VValue* DBPROP может относиться любой из нескольких типов. *VValue.vt* должен задавать тип, совместимый с типом данных столбца. Например, если столбец имеет тип DBTYPE_WSTR и для этого столбца задано значение по умолчанию BSTR N/A, эти два типа совместимы. Определение же значение по умолчанию на столбец, определенный как DBTYPE_R8 приводит к ошибке при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается создать таблицу на сервере.|  
|DBPROP_COL_DESCRIPTION|И запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: Свойство столбца DBPROP_COL_DESCRIPTION не реализован [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.<br /><br /> *DwStatus* член структуры DBPROP возвращает значение DBPROPSTATUS_NOTSUPPORTED при попытке потребителя записать значение свойства.<br /><br /> Задание свойства не является неустранимой ошибкой для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента. Если все остальные значения параметров допустимы, таблица [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет создана.|  
|DBPROP_COL_FIXEDLENGTH|И запись: чтение и запись<br /><br /> По умолчанию: VARIANT_FALSE<br /><br /> Описание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента использует значение DBPROP_COL_FIXEDLENGTH для определения сопоставления типов данных, когда потребитель задает тип данных столбца с помощью *wType* структуры DBCOLUMNDESC. Дополнительные сведения см. в разделе [сопоставления типов данных в интерфейсе ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).|  
|DBPROP_COL_NULLABLE|И запись: чтение и запись<br /><br /> По умолчанию: нет<br /><br /> Описание: При создании таблицы, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента указывает, должен ли столбец принимать значения null, если свойство имеет значение. Когда свойство не задано, способность столбца принимать значения NULL определяется установленным по умолчанию параметром базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ANSI_NULLS.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента является поставщик соответствует требованиям стандарта ISO. Подключенные сеансы ведут себя в соответствии со стандартом ISO. Если потребитель не задал свойство DBPROP_COL_NULLABLE, столбец принимает значения NULL.|  
|DBPROP_COL_PRIMARYKEY|И запись: чтение и запись<br /><br /> Значение по умолчанию — Значение VARIANT_FALSE Описание: Если значение VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента создает столбец с ограничением PRIMARY KEY.<br /><br /> При задании в качестве свойства столбца только один столбец может определять это ограничение. Установка этого свойства в VARIANT_TRUE сложнее, чем один столбец возвращает сообщение об ошибке при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается создать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.<br /><br /> Примечание: Потребитель может использовать **IIndexDefinition::CreateIndex** для создания ограничения PRIMARY KEY на два или несколько столбцов.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение DB_S_ERRORSOCCURRED, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* свойства DBPROP_COL_UNIQUE не равен DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE, то возвращается ошибка DB_E_ERRORSOCCURRED и *dwOption* свойства DBPROP_COL_UNIQUE равен DBPROPOPTIONS_REQUIRED. Столбец определяется с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство identity, а элементу DBPROP_COL_PRIMARYKEY *dwStatus* устанавливается значение DBPROPSTATUS_CONFLICTING.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает ошибку, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_NULLABLE имеют значение VARIANT_TRUE.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает ошибку из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если потребитель пытается создать ограничение PRIMARY KEY для столбца недопустимого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных. Ограничения PRIMARY KEY нельзя определять для столбцов, созданных с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных **бит**, **текст**, **ntext**, и **изображение**.|  
|DBPROP_COL_UNIQUE|И запись: чтение и запись<br /><br /> Значение по умолчанию — Значение VARIANT_FALSE Описание: применяется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ограничение УНИКАЛЬНОСТИ для столбца.<br /><br /> При задании в качестве свойства столбца только к одному столбцу может быть применено это ограничение. Потребитель может использовать **IIndexDefinition::CreateIndex** для создания ограничения UNIQUE на сочетании значений двух или нескольких столбцов.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение DB_S_ERRORSOCCURRED, если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* не равен DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_PRIMARYKEY и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE, то возвращается ошибка DB_E_ERRORSOCCURRED и *dwOption* равен DBPROPOPTIONS_REQUIRED. Столбец определяется с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство identity, а элементу DBPROP_COL_PRIMARYKEY *dwStatus* устанавливается значение DBPROPSTATUS_CONFLICTING.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает значение DB_S_ERRORSOCCURRED, если оба свойства DBPROP_COL_NULLABLE и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE и *dwOption* не равен DBPROPOPTIONS_REQUIRED.<br /><br /> Если оба свойства DBPROP_COL_NULLABLE и DBPROP_COL_UNIQUE имеют значение VARIANT_TRUE, то возвращается ошибка DB_E_ERRORSOCCURRED и *dwOption* равен DBPROPOPTIONS_REQUIRED. Столбец определяется с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] свойство identity и DBPROP_COL_NULLABLE *dwStatus* устанавливается значение DBPROPSTATUS_CONFLICTING.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает ошибку из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если потребитель пытается создать ограничение уникальности для столбца недопустимого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных. Ограничения UNIQUE нельзя определять для столбцов, созданных с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **бит** тип данных.|  
  
 Когда потребитель вызывает **ITableDefinition::CreateTable**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента интерпретирует свойства таблицы следующим образом.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|И запись: чтение и запись<br /><br /> Значение по умолчанию — Значение VARIANT_FALSE Описание: по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента создает таблицы, имена которых присваивает потребитель. Если значение VARIANT_TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента создает имя временной таблицы для потребителя. Потребитель устанавливает *pTableID* параметр **CreateTable** значение NULL. *PpTableID* параметр должен содержать допустимый указатель.|  
  
 Если потребитель запрашивает, что открыть набор строк для успешно созданной таблицы, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента открывает набор строк, поддерживаемый курсорами. Все свойства набора строк могут быть заданы в передаваемых наборах свойств.  
  
 В данном примере создается таблица [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
// This CREATE TABLE statement shows the details of the table created by   
// the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//    CONSTRAINT PK_OrderDetails  
//         PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
// The PRIMARY KEY constraint is created in an additional example.  
HRESULT CreateTable  
    (  
    ITableDefinition* pITableDefinition  
    )  
    {  
    DBID            dbidTable;  
    const ULONG     nCols = 5;  
    ULONG           nCol;  
    ULONG           nProp;  
    DBCOLUMNDESC    dbcoldesc[nCols];  
  
    HRESULT         hr;  
  
    // Set up column descriptions. First, set default property values for  
    //  the columns.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbcoldesc[nCol].pwszTypeName = NULL;  
        dbcoldesc[nCol].pTypeInfo = NULL;  
        dbcoldesc[nCol].rgPropertySets = new DBPROPSET;  
        dbcoldesc[nCol].pclsid = NULL;  
        dbcoldesc[nCol].cPropertySets = 1;  
        dbcoldesc[nCol].ulColumnSize = 0;  
        dbcoldesc[nCol].dbcid.eKind = DBKIND_NAME;  
        dbcoldesc[nCol].wType = DBTYPE_I4;  
        dbcoldesc[nCol].bPrecision = 0;  
        dbcoldesc[nCol].bScale = 0;  
  
        dbcoldesc[nCol].rgPropertySets[0].rgProperties =   
            new DBPROP[NCOLPROPS_MAX];  
        dbcoldesc[nCol].rgPropertySets[0].cProperties = NCOLPROPS_MAX;  
        dbcoldesc[nCol].rgPropertySets[0].guidPropertySet =  
            DBPROPSET_COLUMN;  
  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                dwOptions = DBPROPOPTIONS_REQUIRED;  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].colid  
                 = DB_NULLID;  
  
            VariantInit(  
                &(dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                    vValue));  
  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt = VT_BOOL;  
            }  
        }  
  
    // Set the column-specific information.  
    dbcoldesc[0].dbcid.uName.pwszName = L"OrderID";  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[0].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[1].dbcid.uName.pwszName = L"ProductID";  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[1].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[2].dbcid.uName.pwszName = L"UnitPrice";  
    dbcoldesc[2].wType = DBTYPE_CY;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[2].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[3].dbcid.uName.pwszName = L"Quantity";  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[3].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[4].dbcid.uName.pwszName = L"Discount";  
    dbcoldesc[4].wType = DBTYPE_NUMERIC;  
    dbcoldesc[4].bPrecision = 2;  
    dbcoldesc[4].bScale = 2;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].dwPropertyID =   
        DBPROP_COL_DEFAULT;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.vt = VT_BSTR;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.bstrVal =  
        SysAllocString(L"0");  
    dbcoldesc[4].rgPropertySets[0].cProperties = 2;  
  
    // Set up the dbid for OrderDetails.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    if (FAILED(hr = pITableDefinition->CreateTable(NULL, &dbidTable,  
        nCols, dbcoldesc, NULL, 0, NULL, NULL, NULL)))  
        {  
        DumpError(pITableDefinition, IID_ITableDefinition);  
        goto SAFE_EXIT;  
        }  
  
SAFE_EXIT:  
    // Clean up dynamic allocation in the property sets.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            if (dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt == VT_BSTR)  
                {  
                SysFreeString(dbcoldesc[nCol].rgPropertySets[0].  
                    rgProperties[nProp].vValue.bstrVal);  
                }  
            }  
  
        delete [] dbcoldesc[nCol].rgPropertySets[0].rgProperties;  
        delete [] dbcoldesc[nCol].rgPropertySets;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>См. также  
 [Таблицы и индексы](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
