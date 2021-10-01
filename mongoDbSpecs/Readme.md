# Steps to setup Mongo DB

##### Followed URL - https://faun.pub/managing-mongodb-on-docker-with-docker-compose-26bf8a0bbae3

## Steps 
1. docker pull mongo:latest
2. Create docker file with credentials
3. docker-compose up / docker-compose up -d 
4. docker exec -it mong_db bash
5. mongo -u root -p example
6. mongodb://root:example@127.0.0.1:27017/de_framework
7. use DeApp
8. db.rtl_crf_dim_card.insertOne(
    {id:"12345",email:"pradeep@maf.com",phone:"585974570"}
    )
9. db.app_params.insertMany([
    {_id : 1 ,
    DataSet:"rtl_crf_dim_card",
    SourceToParsed:{s3Location:"data-ingestion/CRF/Fact",FileRegx:"crf_dim_card",Archive:"Y",Unzip:"Y",ProtectFile:"N"},
    ParsedToStg:{s3Location:"data-ingestion/CRF/Fact",FileRegx:"crf_dim_card",STGTable:"CA_STG.stg_crf_dim_card",DBConnName:"VerticaDB"},
    StgToOds:{STGTable:"CA_STG.stg_crf_dim_card",SCDLogic:"Dim/Fact",ODSTable:"CA_ODS.ods_crf_dim_card",DBConnName:"VerticaDB"},
    ExecuteParams:["SourceToParsed","ParsedToStg","StgToOds"]
    },
    {_id : 2 ,
    DataSet:"rtl_crf_dim_account",
    SourceToParsed:{s3Location:"data-ingestion/CRF/Fact",FileRegx:"crf_dim_account",Archive:"Y",Unzip:"Y",ProtectFile:"N"},
    ParsedToStg:{s3Location:"data-ingestion/CRF/Fact",FileRegx:"crf_dim_account",STGTable:"CA_STG.stg_crf_dim_account",DBConnName:"VerticaDB"},
    StgToOds:{STGTable:"CA_STG.stg_crf_dim_account",SCDLogic:"Dim/Fact",ODSTable:"CA_ODS.ods_crf_dim_account",DBConnName:"VerticaDB"},
    ExecuteParams:["SourceToParsed","ParsedToStg","StgToOds"]
    }]
    )
db.rtl_crf_dim_account.insertOne(
    )
10. db.rtl_crf_dim_card.deleteOne(
    {_id : 1}
    )
11. db.rtl_crf_dim_card.updateOne( { _id: 608db3f88a81dbf762151484 }, [ { $set: { phone: "585974571", DateTime: "$$NOW"} } ] )
12. 
db.app_params.insertMany([{
    "value": {
        "dataSetName": "rtl_crf_dim_card",
        "s3SourceToParsed": {
            "s3Location": "data-ingestion/CRF/Factssss",
            "FileRegx": "rtl_crf_dim_card",
            "Archive": "Y",
            "Unzip": "Y",
            "ProtectFile": "N"
        },
        "ParsedToStg": {
            "s3Location": "data-ingestion/CRF/Fact",
            "FileRegx": "rtl_crf_dim_card",
            "STGTable": "CA_STG.stg_crf_dim_account",
            "DBConnName": "VerticaDB"
        },
        "StgToOds": {
            "STGTable": "CA_STG.stg_crf_dim_account",
            "SCDLogic": "Dim/Fact",
            "ODSTable": "CA_ODS.ods_crf_dim_account",
            "DBConnName": "VerticaDB"
        },
        "ExecuteParams": [
            "s3SourceToParsed",
            "ParsedToStg",
            "StgToOds"
        ]
    }
},
{
    "value": {
        "dataSetName": "rtl_crf_dim_account",
        "s3SourceToParsed": {
            "s3Location": "data-ingestion/CRF/Factssss",
            "FileRegx": "rtl_crf_dim_account",
            "Archive": "Y",
            "Unzip": "Y",
            "ProtectFile": "N"
        },
        "ParsedToStg": {
            "s3Location": "data-ingestion/CRF/Fact",
            "FileRegx": "rtl_crf_dim_account",
            "STGTable": "CA_STG.stg_crf_dim_account",
            "DBConnName": "VerticaDB"
        },
        "StgToOds": {
            "STGTable": "CA_STG.stg_crf_dim_account",
            "SCDLogic": "Dim/Fact",
            "ODSTable": "CA_ODS.ods_crf_dim_account",
            "DBConnName": "VerticaDB"
        },
        "ExecuteParams": [
            "s3SourceToParsed",
            "ParsedToStg",
            "StgToOds"
        ]
    }
},
{
    "value": {
        "dataSetName": "rtl_crf_dim_customer",
        "s3SourceToParsed": {
            "s3Location": "data-ingestion/CRF/Factssss",
            "FileRegx": "crf_dim_customer",
            "Archive": "Y",
            "Unzip": "Y",
            "ProtectFile": "N"
        },
        "ParsedToStg": {
            "s3Location": "data-ingestion/CRF/Fact",
            "FileRegx": "crf_dim_customer",
            "STGTable": "CA_STG.stg_crf_dim_account",
            "DBConnName": "VerticaDB"
        },
        "StgToOds": {
            "STGTable": "CA_STG.stg_crf_dim_account",
            "SCDLogic": "Dim/Fact",
            "ODSTable": "CA_ODS.ods_crf_dim_account",
            "DBConnName": "VerticaDB"
        },
        "ExecuteParams": [
            "s3SourceToParsed",
            "ParsedToStg",
            "StgToOds"
        ]
    }
}
])
