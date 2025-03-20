const http=require('http');
const fs =require('fs');
const path=require('path');

const port=3000;

const server=http.createServer((req,res)=>{
   const filepath= path.join(__dirname, req.url === '/' ? "index.html" : req.url);
   console.log(filepath);
   

   const ext=String(path.extname(filepath)).toLowerCase();
   const mimeType={
    '.html':'text/html',
    '.css':'text/css',
    '.js':'text/js',
   }

  const contentType= mimeType[ext] || 'application/octet-stream';

  fs.readFile(filepath,(err,content)=>{
    if(err){
        if(err.code === "ENOENT"){
            res.writeHead(404,{'content-Type':"text/html"})
            res.end("404: file not found brooo");
        }
    }else{
        res.writeHead(200,{'content-Type':contentType});
        res.end(content,'utf-8');
    }
  });
});//request ans response

server.listen(port,()=>{
    console.log(`server is listening on port ${port}` );
    
})
