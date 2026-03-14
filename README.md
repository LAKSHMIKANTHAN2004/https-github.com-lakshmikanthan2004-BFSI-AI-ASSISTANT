app.py
       from fastapi import FastAPI
from pydantic import BaseModel
from services.response_pipeline import process_query


app=FastAPI()


class Query(BaseModel):


    question:str


@app.post("/ask")


def ask(q:Query):


    answer=process_query(q.question)


    return {"response":answer}
Run server:
uvicorn app:app --reload
Test:
POST http://localhost:8000/ask
Body:
{
 "question":"What is EMI calculation?"
}
