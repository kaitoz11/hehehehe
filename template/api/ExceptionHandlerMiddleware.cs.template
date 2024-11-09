using System.Threading.Tasks;
using Microsoft.AspNetCore.Http;
using Microsoft.AspNetCore.Mvc;
using System.Threading;
using System;

namespace API.Middlewares
{
    public class ExceptionHandlerMiddleware : IMiddleware
    {
        public async Task InvokeAsync(HttpContext httpContext, RequestDelegate next)
        {
            try
            {
                // Proceed with the request
                await next(httpContext);
            }
            catch (Exception exception)
            {
                // Handle exceptions by creating a ProblemDetails response
                var response = new ProblemDetails
                {
                    Status = StatusCodes.Status500InternalServerError,
                    Type = exception.GetType().Name,
                    Title = "Internal server error",
                    Detail = exception.Message,
                    Instance = $"{httpContext.Request.Method} {httpContext.Request.Path}"
                };

                httpContext.Response.StatusCode = response.Status ?? StatusCodes.Status500InternalServerError;
                httpContext.Response.ContentType = "application/json";
                await httpContext.Response.WriteAsJsonAsync(response);
            }
        }
    }
}
