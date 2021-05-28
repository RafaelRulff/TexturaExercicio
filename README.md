# TexturaExercicio

void Sphere(float radius, int n_lat, int n_lon)

{

    glEnable(GL_LIGHTING);
    
glEnable(GL_TEXTURE_2D); 

glTexParameterf(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT); 

glTexParameterf(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);

glTexParameterf(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_NEAREST); 

glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_NEAREST);

    TextureManager::Inst()->BindTexture(1);

    glBegin(GL_TRIANGLES);
    
for (float i = 0; i < n_lat; i += 1.f)

    for (float j = 0; j < n_lon; j += 1.f)
    
    {
    
        Vector3 p;
        
        GLfloat u;
        
        GLfloat v;
        
        // -- primeiro triangulo
        
        p = SphereCoord(i, j, n_lat, n_lon);
        
                glNormal3(p);

        u=atan2f(p.y,p.x)/2*PI+0.5;
        
        v=0.5-asinf(p.z)/PI;
        
        glTexCoord2f(u,v);

        glVertex3(p * radius);

        p = SphereCoord(i + 1, j, n_lat, n_lon);
        
        glNormal3(p);

        u=atan2f(p.y,p.x)/2*PI+0.5;
        
        v=0.5-asinf(p.z)/PI;
        
        glTexCoord2f(u,v);

        glVertex3(p * radius);


        p = SphereCoord(i + 1, j + 1, n_lat, n_lon);
        
        glNormal3(p);

        u=atan2f(p.y,p.x)/2*PI+0.5;
        
        v=0.5-asinf(p.z)/PI;
        
        glTexCoord2f(u,v);

        glVertex3(p * radius);



        // -- segundo triangulo
        
        p = SphereCoord(i, j, n_lat, n_lon);
        
                glNormal3(p);

        u=atan2f(p.y,p.x)/2*PI+0.5;
        
        v=0.5-asinf(p.z)/PI;
        
        glTexCoord2f(u,v);

        glVertex3(p * radius);



        p = SphereCoord(i + 1, j + 1, n_lat, n_lon);
        
        glNormal3(p);

        u=atan2f(p.y,p.x)/2*PI+0.5;
        
        v=0.5-asinf(p.z)/PI;
        
        glTexCoord2f(u,v);
        

        glVertex3(p * radius);


        p = SphereCoord(i, j + 1, n_lat, n_lon);
        
        glNormal3(p);

        u=atan2f(p.y,p.x)/2*PI+0.5;
        
        v=0.5-asinf(p.z)/PI;
        
        glTexCoord2f(u,v);

        glVertex3(p * radius);
        
}

glEnd();

}
